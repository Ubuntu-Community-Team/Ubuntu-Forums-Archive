---
title: "how to enable my wireless device using toshiba laptop"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by quecoder on 2008-02-29
hello ,
I have just installed ubuntu :):) , and i'm now using toshiba satellite A100 , and I don't know how to enable the wireless , to read online help while using the ubuntu ..
I don't know **any** thing in linux system , so please help !

---

### Post by anewguy on 2008-02-29
First we need to know which wireless adapter you have, then we can move on with instructions for getting it running.  To find what adapter you have, please do the following:

Open a terminal window via Applications/Accessories/Terminal

type in the following, then press "Enter":

lspci


Use your mouse and copy the output text, then open a reply here and paste it.

Thanks :)

---

### Post by quecoder on 2008-02-29
> **anewguy said:**
> First we need to know which wireless adapter you have, then we can move on with instructions for getting it running.  To find what adapter you have, please do the following:

Open a terminal window via Applications/Accessories/Terminal

type in the following, then press "Enter":

lspci


Use your mouse and copy the output text, then open a reply here and paste it.

Thanks :)

Hi anewguy :) , thanks for your help v much .. but , is not there , please , any other way to do so in windows ? because i'm now working on it where I have internet connection with wireless working properly :) 
thanks again

---

### Post by kool_kat_os on 2008-02-29
> **quecoder said:**
> Hi anewguy :) , thanks for your help v much .. but , is not there , please , any other way to do so in windows ? because i'm now working on it where I have internet connection with wireless working properly :) 
thanks again

waht do you mean "it's not there"???

---

### Post by quecoder on 2008-03-01
Intel(R) PRO/Wireless 3945ABG Network Connection
can this help ? :)

---

### Post by quecoder on 2008-03-01
> **kool_kat_os said:**
> waht do you mean "it's not there"???

I meant , "is not there any other way to.. "
Bad english + typos ...

---

### Post by kool_kat_os on 2008-03-01
> **quecoder said:**
> I meant , "is not there any other way to.. "
Bad english + typos ...

ok...its ok...now i get it:)

---

### Post by quecoder on 2008-03-01
> **kool_kat_os said:**
> ok...its ok...now i get it:)

:)

---

### Post by anewguy on 2008-03-01
If you are currently running Windows, go in to device manager and check the wireless adapter there - it should give you the manufacturer and possibly list the drivers as well.

---

### Post by quecoder on 2008-03-01
anewguy , I think it is Intel(R) PRO/Wireless 3945ABG .

---

### Post by anewguy on 2008-03-01
If that's the case, it appears you can use the restricted drivers and blacklist the ipv6 driver and it should work.  Please read through this post, then try what it suggests and post back.

[http://ubuntuforums.org/showthread.php?t=398949&page=2]("http://ubuntuforums.org/showthread.php?t=398949&page=2")



BTW - for anyone who might read this post - there are MANY entries for this and other questions if you just search Yahoo! or Google.  I found this information just doing the following search on Yahoo:

ubuntu intel pro wireless 3945abg

If you put the OS first, you'll return these types of links.

At any rate, post back if you continue to have problems.

:)

---

### Post by quecoder on 2008-03-01
> **anewguy said:**
> If that's the case, it appears you can use the restricted drivers and blacklist the ipv6 driver and it should work.  Please read through this post, then try what it suggests and post back.

[http://ubuntuforums.org/showthread.php?t=398949&page=2]("http://ubuntuforums.org/showthread.php?t=398949&page=2")



BTW - for anyone who might read this post - there are MANY entries for this and other questions if you just search Yahoo! or Google.  I found this information just doing the following search on Yahoo:

ubuntu intel pro wireless 3945abg

If you put the OS first, you'll return these types of links.

At any rate, post back if you continue to have problems.

:)
Thanksss alot anewguy :) i'll do it now .. stay tuned ,, lol

---

### Post by tad1073 on 2008-03-01
If your in windows I think yu can do:
```
ipconfig /all
```
from the command prompt

---

### Post by quecoder on 2008-03-01
> **tad1073 said:**
> If your in windows I think yu can do:
```
ipconfig /all
```
from the command prompt

I run this command in cmd , and it returned exactly what I thought ... thanks for this quick method :)

---

### Post by baxterdog on 2008-03-01
also type

lspci

in your terminal.

---

### Post by anewguy on 2008-03-01
Any luck yet?

---

