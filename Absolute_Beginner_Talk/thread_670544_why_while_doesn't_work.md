---
title: "why while doesn't work?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by kantze on 2008-01-17
Hi there. I'm very new to shell programming.

I've copied this code 
```

#!/bin/sh
INPUT_STRING=hello
while [ "$INPUT_STRING" != "bye" ]
do
  echo "Please type something in (bye to quit)"
  read INPUT_STRING
  echo "You typed: $INPUT_STRING"
done

``` from here:[http://steve-parker.org/sh/loops.shtml](http://steve-parker.org/sh/loops.shtml)

but when I tried to run it, it displayed these messages:
```

"./while.sh: 3: while [: not found
"./while.sh" 4: Syntax error: "do" unexpected

```

Can you please tell me what should I do?

---

### Post by stevescripts on 2008-01-17
duh ... it works for me in bash as written ...

what shell are you using, and how did you invoke the script?

Steve

---

### Post by mali2297 on 2008-01-17
It works fine for me as well. :-s

---

### Post by sisco311 on 2008-01-17
funny but works for me. try to replace #!/bin/sh with #!/bin/bash

---

### Post by mali2297 on 2008-01-17
Have you missed the space after *while*?
That gave me the same error.

---

### Post by kantze on 2008-01-17
I'm using Ubuntu 7.10. The shell I think is Bourne/Bash shell. I'm calling the script writing

```

./while.sh

```
in the terminal and I've given to it the rights to be executed...

---

### Post by kantze on 2008-01-17
> **mali2297 said:**
> Have you missed the space after *while*?
That gave me the same error.

Well, it seems that this was the problem! Thank you, I didn't noticed it...

---

### Post by mali2297 on 2008-01-17
> **kantze said:**
> I'm using Ubuntu 7.10. The shell I think is Bourne/Bash shell. I'm calling the script writing

```

./while.sh

```
in the terminal and I've given to it the rights to be executed...

The line
```

#!/bin/sh

```
tells the system to run /bin/sh which in ubuntu links to [dash]("http://en.wikipedia.org/wiki/Debian_Almquist_shell").

---

