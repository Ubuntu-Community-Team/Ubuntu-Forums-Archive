---
title: "X700 Radeon Issue Question"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by kingspan on 2007-06-05
Hi,

I read the Installing Ubuntu 7.04: ATI X***** Cards.  

I am trying to install and getting a Fatal Service Error No Screens Found.  I810.  From my research on the web, it sounds as if it is from the error above.  

I have the Live CD of 7.04.  The fix posed by Mike says to use the Alternate CD, which I am now downloading.  My question is if I can't install with the live CD because of this error, aren't I going to get the same error when I try to install from the Alternate CD?  if so, I can not complete the install as instructed by Mike.  

I am EXTREMELY new to Linux but really want to learn it.

I appreciate any help in advance.

Thank you,

Kingspan

---

### Post by Znupi on 2007-06-05
You will be able to install it using the Alternate CD.

But I don't think it will work once installed, you might need to some extra stuff. Try the Alternate CD and tell us what happens :).

---

### Post by kingspan on 2007-06-06
Ok I installed Ubunto on my drive through the altnerate CD, did everything Mike said to do and I still get the same error.  So you were correct, there is more I need to do.  :D

---

### Post by Edgewalker_001 on 2007-06-06
I have the same problem on the same graphics card, I used an old CD for the actual installation and then upgraded to 7.04, no problems with the 6.06 version, no problems with 6.10 and then when I rebooted after installation of 7.04 the whole 
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration.

Error message popped up.

I tried inputing the command lines that the stickied post recommended and they seemed to install OK, then the next time I rebooted the screen just goes black after the Ubuntu loading screen and the entire computer seem to simply stop working (Not even a flicker of HD access)

I'm at a loss on what to do...

---

### Post by kingspan on 2007-06-06
Does 7.04 give us better usability?  I am wondering if I should download the older versions and try them since they seem to work for you.  I want to learn how to use Ubuntu but if I can't get it loaded, that won't help.

---

### Post by Edgewalker_001 on 2007-06-06
Ok... I fixed it myself using some spit n' glue and the (VERY) handy [PHP]sudo dpkg-reconfigure xserver-xorg[/PHP] command.

---

### Post by kingspan on 2007-06-06
I have  no clue what I did but I ran through your command and it worked.  Thank you!

Garry:KS

---

