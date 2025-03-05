---
title: "CREATE-CHATBOT"
date: 2025-03-05
---

I want to make chatbot!
because, I want to try using API.

there are various APIs,"openAI","amazon",google",etc.

I select "OPENAI API".
Because, I always use chatGPT.

first,create an API_key in dashboard
```python
export OPENAI_API_KEY="your_api_key_here"
```

second,to use the OpenAI API in python. Get started by installing the SDK using pip
```python
pip install openai
```

last,create a file. and,make a chatbot:Create a human-like response to a prompt
```python
from openai import OpenAI
client = OpenAI()

completion = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {
            "role": "user",
            "content": "Write a haiku about recursion in programming."
        }
    ]
)

print(completion.choices[0].message)
```

output 

ChatCompletionMessage(content='Functions call themselves,  \nLayers deep in logic’s dance—  \nInfinite embrace.', refusal=None, role='assistant', audio=None, function_call=None, tool_calls=None)

this output is difficult to understand.
so,add content to print( ).
```python
from openai import OpenAI
client = OpenAI()

completion = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {
            "role": "user",
            "content": "Write a haiku about recursion in programming."
        }
    ]
)

print(completion.choices[0].message.content)
```

output

Functions call themselves,  
Layers deep in logic’s dance—  
Infinite embrace.

Now,output is easy to understand.

Another question is "What's the population of the United States?"
Updata content
```python
from openai import OpenAI
client = OpenAI()

completion = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {
            "role": "user",
            "content": "What's the population of the United States?"
        }
    ]
)

print(completion.choices[0].message.content)
```
