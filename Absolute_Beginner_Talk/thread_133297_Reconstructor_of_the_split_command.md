---
title: "Reconstructor of the split command"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by Ben Stamper on 2006-02-19
I need to know the command that will reconstruct a file that has been split. Not exactly a beginner question, but it seemed like the best place.

---

### Post by heimo on 2006-02-20
Not sure if this is what you're looking for - an example:


```
echo "foo" > a
echo "bar" > b
[B]cat a b > c
[/B]cat c

```

output:
> foo
bar


---

