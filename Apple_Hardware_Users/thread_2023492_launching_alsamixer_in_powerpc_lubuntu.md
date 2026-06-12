---
title: "launching alsamixer in powerpc lubuntu?"
date: 2012-07-12
forum: Apple Hardware Users
---

### Post by 2blue on 2012-07-12
Has anyone with lubuntu powerpc build 12.04 managed to launch alsamixer in terminal? I have no sound, and no access to system audiosettings, either on system panel or terminal. It os a bit weird, and I was wondering if it was a bug of some sort. 

I cannot make Java run either, though the packages are installed and show in package manager. 

Any thoughts on what the issue can be? 

Regards

---

### Post by rsavage on 2012-07-13
As far as I know there are no problems with alsamixer. What is the exact error message you get?
 
Ditto Openjdk Java. Are you running from the terminal or web browser? I've noticed if you are running an applet you often get a grey box until it has finished loading. IBM Java's plugin seems to work better (you don't get the grey box). If you are a Java enthusiast then you should contact IBM and tell them their Java 7 is broken.
 
What is the output of
 
```

echo $PATH 

```
 
On another thread you wrote 
 
> 
With the gecko plugin I have aslo been able to stream live TV.

 
Can you expand on the above please? Is that gecko media player you are talking about? On powerpc? I've yet to get it to work in modern versions of firefox so would be interested. Thanks

---

### Post by 2blue on 2012-07-13
Thanks for reply. I was given help for the alsa-trouble, and it turnd out to be some kind of config blacklist issue, that was sorted out with a simple command in terminal and reboot.

I have another, (possibly embarresing) trouble with copy&paste issues, and some signs on the keyboard like the dollar sign will not appear. I`m used to copy and paste by either holding down the "apple-key", or "apple-key ctrl" simultaneously, in combination with either regular "C" and "V". 

For the dollar sign, it doesn`t help what ever I hold down, either apple key; apple key - ctrl; tab.... I have Norwegian keyboard settings and the dollar sign are on the number 4 key together with the Euro sign, and what ever keys I hold down all I get is either 4 or ¤. 

The sign issue and copy&paste issue can make sudo commands rather difficult.

Sorry for not making it clearer; I`ve used the gecko-plugin setup previously on regular pcs, not ppc. This is my first venture with linux on ppc. The gecko setup should run with Firefox 13 i think, I will check with my other computer as soon as possible. I assumed it would be much the same for ppc though.

---

