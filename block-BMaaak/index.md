writeCode

Q1. Create an userSchema which has fields

- name
- username
- email
- address {
  - city
  - state
  - country
  - pin
    }
```js
let userSchema = new Schema({
  name: String,
  username:String,
  email:String,
  address: {
    city:String,
    state:String,
    country:String,
    pin:Number,
  }
})

userSchema.index( { username: 1, email: 1 }, { unique: true } )

userSchema.index({"address.country":1 , "address.state":1})

```
1. Define unique indexes on username and email.
2. define compound indexes on state and country field inside address document. Each country must have states which are unique.

Q2. Create an article Schema with fields

- title
- description
- tags[String]

1. Add multikey indexes on tags which is an array of strings
2. Add text indexes on title as users will search for texts present in an article's title.
3. Update text indexes to include descriptions as well. Implement text indexes on both title and description.
```js
let article = new Schema({
  title:String,
  description:String,
  tags:[String]
})

article.index({tags:1})
article.index({title:"text", description:"text"})
```