---
title: "argument list too long"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by james_027 on 2007-05-20
Hi,

Iam trying to execute this command 

 sudo chmod +x `sudo find eclipse -type d`

and I am getting this error ... argument list too long

help?:(](*,)

---

### Post by seshomaru samma on 2007-05-20
looks like a combination of two commands

what are you trying to do?
are you following some guide?
chmod command changes permissions - which permissions are you trying to change?

---

### Post by jyba on 2007-05-20
It looks as if the list that the find command is producing is taking up too much memory. There's a good FAQ about it here:

[http://www.gnu.org/software/coreutils/faq/#Argument-list-too-long](http://www.gnu.org/software/coreutils/faq/#Argument-list-too-long)

The solution is to use xargs to control the flow of output from find to chmod like this:

```
sudo find eclipse -type d -print0 | xargs -0 sudo chmod +x
```

---

### Post by james_027 on 2007-05-20
> **seshomaru samma said:**
> looks like a combination of two commands

what are you trying to do?
are you following some guide?
chmod command changes permissions - which permissions are you trying to change?

yes, I am trying to follow [this guide]("http://flurdy.com/docs/eclipse/install.html")

> **jyba said:**
> It looks as if the list that the find command is producing is taking up too much memory. There's a good FAQ about it here:

[http://www.gnu.org/software/coreutils/faq/#Argument-list-too-long](http://www.gnu.org/software/coreutils/faq/#Argument-list-too-long)

The solution is to use xargs to control the flow of output from find to chmod like this:

```
sudo find eclipse -type d -print0 | xargs -0 sudo chmod +x
```

I have try your suggestion but the same error  occur ...

:(:(:(

---

### Post by jyba on 2007-05-21
Okay, try:
```

sudo find eclipse -type d -print0 | xargs -I{} -0 sudo chmod +x {}
```

Let me know if it doesn't work. I'm off to bed in an hour's time, so after that your on your own. :)

---

### Post by james_027 on 2007-05-21
> **jyba said:**
> Okay, try:
```

sudo find eclipse -type d -print0 | xargs -I{} -0 sudo chmod +x {}
```

Let me know if it doesn't work. I'm off to bed in an hour's time, so after that your on your own. :)

Thanks very much it works. could you explain to me what was done?

I know chmod is for changing permission, I don't why the chmod was executed that way ... with find exlipse -type d. I don't get the idea.

sudo chmod +x `sudo find eclipse -type d`

Thanks again :popcorn:

james

---

