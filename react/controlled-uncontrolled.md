# [React] controlled vs uncontrolled component

## πΒ λΉμ μ΄ μ»΄ν¬λνΈ (uncontrolled component)

`λΉμ μ΄ μ»΄ν¬λνΈ` μμ νΌ λ°μ΄ν°λ DOM μμ²΄μ μ μ₯λ©λλ€.

λ§μ½ ν΄λΉ νΌ λ°μ΄ν°λ₯Ό μ½μ΄μ€κ³  μΆλ€λ©΄ `ref` λ₯Ό μ΄μ©ν΄μ **κ°μ `PULL` ν΄μμ** μ¬μ©ν©λλ€.

```jsx
import React, { useRef } from 'react'

const UnControlledComponent = () => {
  const inputRef = useRef(null)

  const handleClick = () => {
    /** input κ°μΌλ‘ νΉμ  λ‘μ§μ μνν©λλ€. */
    console.log(inputRef.current.value)
  }

  return (
    <div>
      <input type="text" ref={inputRef} />
      <button onClick={handleClick} >νμΈ</button>
    </div>
  )
}

export default UnControlledComponent
```

## πΒ μ μ΄ μ»΄ν¬λνΈ (controlled component)

`μ μ΄ μ»΄ν¬λνΈ` λ λ³΄λ€ `Reactμ€λ¬μ΄ λ°©λ²` μΌλ‘ κ°μ μ μ΄ν©λλ€.

`React` μ»΄ν¬λνΈμ μνκ°μ `μ λ’° κ°λ₯ν λ¨μΌ μΆμ² (single source of truth)` λ‘ λ§λ€μ΄ μ¬μ©ν©λλ€.

νΌ μλ ₯ μ»΄ν¬λνΈμ `value` κ° ν΄λΉ μ»΄ν¬λνΈμ `state` μμ κ΄λ¦¬λλ©° λκΈ°νλλ λ°©μμλλ€.

```jsx
import React, { useState } from 'react'

const ControlledComponent = () => {
  const [ name, setName ] = useState('')

  const handleChange = (event) => {
    setName(event.target.value )
  }

  return (
    <div>
      <input type="text" value={name} onChange={handleChange} />
    </div>
  )
}

export default ControlledComponent
```

μλ ₯κ°μ λ³νκ° μκΈΈλλ§λ€ `handleChange` ν¨μκ° νΈμΆλμ΄ μνκ°μ΄ λ³ννκ³ 

μ΄λλ¬Έμ λ¦¬λ λλ§μ΄ λ°μν΄ μλ‘μ΄ μνκ°μ΄ `input` μμμ λ°μΈλ© λλ κ²μλλ€.

μ΄λ κ² **μλ‘μ΄ κ°μ `PUSH` νλ λ°©μ**μΌλ‘ κ΅¬ννλ νΌ μλ¦¬λ¨ΌνΈλ₯Ό `μ μ΄ μ»΄ν¬λνΈ` λΌκ³  νλ©° 

μ£Όλ‘ μλ ₯κ°μ μ¦κ°μ μΈ λ³νμ λμνλ λ‘μ§μ μνν΄μΌ νλ κ²½μ°μ μ¬μ©λ©λλ€.

```markdown
*  μλ ₯κ° κ²μ¦ (νμ λ° κ° μ ν¨μ± κ²μ¬)
*  μ ν¨ν κ°μΈμ§ κ²μ¦ ν λ²νΌ νμ±ν λ±μ μν©
```

## πΒ λ μ€ μ΄λκ²μ μ¬μ©ν΄μΌν κΉ?

`useRef` λ₯Ό ν΅ν΄ λΉμ μ΄ μ»΄ν¬λνΈλ₯Ό λ§λ€μ΄ μ¬μ©νλ κ²μ΄ λ¬΄μ‘°κ±΄ λμ κ²μ μλλλ€.

λμ λ°λΌμλ κ°λ³κ³  κ°λ¨ν νΌ μλ¦¬λ¨ΌνΈλ₯Ό λ§λ€κΈ° μν΄ λΉμ μ΄ μ»΄ν¬λνΈλ₯Ό μ¬μ©νλ κ²μ΄ μ μ©ν  μλ μμ΅λλ€.

μ΄μ κ΄λ ¨ν΄μ λ€μκ³Ό κ°μ΄ μ΄λ€ κ²½μ°μ `μ μ΄ νΉμ λΉμ μ΄ μ»΄ν¬λνΈ` λ₯Ό μ¬μ©ν΄μΌν μ§ 

μ§νκ° λ  μ μλ μλ£κ° μμ΄μ μ°Έκ³ νμ¬ νμ©νλ©΄ λ  κ² κ°μ΅λλ€.

![1](https://user-images.githubusercontent.com/37819666/161369274-c8070f92-c05f-4978-ad31-83a4b0b6e022.png)


## πΒ μ°Έκ³ μλ£

[νΌ - React](https://ko.reactjs.org/docs/forms.html#controlled-components)

[Controlled and uncontrolled form inputs in React don't have to be complicated - Gosha Arinich](https://goshacmd.com/controlled-vs-uncontrolled-inputs-react/)