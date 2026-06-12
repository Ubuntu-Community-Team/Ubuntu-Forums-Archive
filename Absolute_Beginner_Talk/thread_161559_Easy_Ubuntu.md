---
title: "Easy Ubuntu"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by namluc on 2006-04-17
I found the easy ubuntu website went to the download page. I assumed that the code that came up was 4 terminal. so opened it up first line
```

sudo apt-get install subversion
```

something good happened - the computer acknowledged it and there were various responses

```

cd ; svn checkout svn://freecontrib.org/easyubuntu
```

What I assume is a download started up. The amount of free space on my hd went down

then the final line
```

gksudo python easyubuntu/trunk/easyubuntu.py
```

and to quote Little Britain i got a "Computer says no" in reply

Which in terminal speak was "what the bloody hell does that mean you fool."

or thereabouts.

So this fool is pretty sure he has some new software on his computer, if only the computer would give it up and pass it over to him.

So i suppose my question is: why didn't code line 3 work and what magic needs to be done to get the computer to give me that sftware?

---

### Post by pbaehr on 2006-04-17
I'm not sure what subversion does, but can you post the actual error for the third command?

Did you install python? I don't think it's part of the default install. If you need to install it:
```
sudo apt-get install python
```

---

### Post by tenn on 2006-04-17
Did you try 
"sudo python easyubuntu/trunk/easyubuntu.py"

---

### Post by namluc on 2006-04-17
That last one worked like a treat thanks.:-D 

Though I've just had a warning box telling me that none of these packages can be authenticated and telling me to beware of malicious individuals. Is easyubuntu not a popular install? And if it is, why can't it be authenticated?

---

### Post by jorn on 2006-04-17
Is there a difference between easy ubuntu and automatix? Don't they handle the same apps. Automatix provides you with more apps.

---

### Post by namluc on 2006-04-17
Well I think that automatix doesn't work on power pcs
sod it gonna install it and see what harm these malicious guys can do:neutral:

---

### Post by namluc on 2006-04-17
downloaded it all and it all seems to have dissapeared again. In a similar position to the gtkpod ap which is currently sitting uselessly on my desktop!
](*,) 
 what am i missing?

apologies 4 my denseness!!!

---

### Post by robotgeek on 2006-04-18
Well, about the warnings..it might have been a problem with the repository keys. 

Try downloading the nightly from [http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html) and tr y the instructions there. 

Soon, all this messy instructions will go away :)

---

