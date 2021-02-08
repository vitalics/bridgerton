# bridgerton

## The Idea

Realize ultimate and realization-independent page object pattern

## High-level API

### Pages

marks with `@Page` decorator
Example

```typescript
@Page({
  url: "/login",
})
class Login {
  email = new Input("#email");
  password = new Input("#password");
  submitButton = new Button("#submit");
}
```

### Component

Marks with `@Component` decorator and initialize type of the variable

Example:

```typescript
@Page({
  url: "/login",
})
class Login {
  form = new Form<UserModel>("#form");
}

// in test
const loginPage = new Login();
loginPage.form.fill({ email: "example@example.com", password: "123" });
loginPage.form.submit();
```

### Basic classes and abstraactions

The Library provides some bacis html elements and interactions

- HTMLComponent - take text, take attribute
- Form<T> - provides a view model of the form. Should be submittable
- Input - html input. Should provides set value
- Button - Clickable element. Hrefs are also buttons
