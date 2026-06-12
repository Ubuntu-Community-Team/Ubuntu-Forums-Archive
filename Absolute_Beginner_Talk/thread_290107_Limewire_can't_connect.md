---
title: "Limewire can't connect"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by youthforlinux on 2006-10-31
My limewire starts but it doesnt connect

---

### Post by disc on 2006-10-31
I have a problem with Limewire as well, when ever I try to run runLime.sh in terminal, I get this error:

./runLime.sh: 44: Syntax error: "(" unexpected (expecting "}")

Any ideas?

---

### Post by plb on 2006-10-31
> **disc said:**
> I have a problem with Limewire as well, when ever I try to run runLime.sh in terminal, I get this error:

./runLime.sh: 44: Syntax error: "(" unexpected (expecting "}")

Any ideas?

You have to open up the limewire script and change /bin/sh to /bin/bash

---

### Post by Dual Cortex on 2006-10-31
Are you using a router?

---

### Post by disc on 2006-10-31
> **plb said:**
> You have to open up the limewire script and change /bin/sh to /bin/bash

I'm still getting the error, you are talking about #!/bin/sh correct?

---

### Post by Bachstelze on 2006-10-31
nope, it's a few lines below, you have a line with *sh <something>*, replace sh with bash.

---

### Post by Dual Cortex on 2006-10-31
Well, seems like this thread has been hijacked ;)

---

### Post by Bachstelze on 2006-10-31
Why ? It's exaclty the same problem :)

---

### Post by Dual Cortex on 2006-10-31
I don't see how they are the same problem... Now I'm hijacking the thread!

---

### Post by angryfirelord on 2006-11-26
Go to /usr/bin/limewire and display its contents (or open it in a text editor). At the line **sh runLime.sh** change the sh to bash. This should execute.

Also, don't forget to install java.

That's what worked for me.

---

### Post by Cardmaster91 on 2006-11-26
this question has been solved many different ways 

[http://ubuntuforums.org/showthread.php?t=306327]("http://ubuntuforums.org/showthread.php?t=306327")

---

