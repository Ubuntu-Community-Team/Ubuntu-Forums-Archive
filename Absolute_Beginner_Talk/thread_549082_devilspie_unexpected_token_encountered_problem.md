---
title: "devilspie unexpected token encountered problem"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by silverace99 on 2007-09-12
So I'm trying to run Devilspie. I want to set it so that gaim starts up automatically in workspace #2.

I make the .ds file, and put it in /home/<user>/.devilspie like the instructions say.

however when I go to a terminal and run devilspie, I get:

> Cannot parse /home/silverace99/.devilspie/gaim.ds: Unexpected token encountered: 226
No s-expressions loaded, quiting

I have been searching and searching for answers and have gotten nowhere, it's quite frustrating. Does anybody know what might cause this?


below is my .ds code:


(if
(is (application_name) “gaim”)
(set_workspace 2)
)

---

### Post by felicity on 2007-09-12
I highly recommend [this article]("http://foosel.org/linux/devilspie") for learning devilspie, it has great examples.

From what I see in your code, maybe you should try this:

```
(if
        (is (application_name) "gaim")
        (begin
               (set_workspace 2)
         )
)
```

---

### Post by silverace99 on 2007-09-12
Yes, that was one of the websites I looked at when I was searching for help. Unfortunately it doesn't provide any hints as to my problem. As far as I can tell, my file text is syntactically in keeping with these "s-expressions".....

---

### Post by felicity on 2007-09-12
Ah, I see what you're saying. I run openbox now so I no longer use devilspie. Maybe there is a blank line at the top of your file? I'm not sure that would affect it but you might check.

---

### Post by silverace99 on 2007-09-12
HUH, you were right on the money

I'm not sure where exactly the blank space or whatever was, but I manually retyped the code and it works now :P

Thanks for your help!

---

### Post by lucraft on 2007-10-18
It was most likely the quotation marks. If you've copied them from a website they are probably the fancy unicode variety.

---

