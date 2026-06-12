---
title: "Installing FX5200 VC. needs instruction on how to?"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Solidad on 2007-07-27
im running Drapper Drake 6.06, i need to install the linux drivers for my VC. since the max resolution im getting is only 1024 x 768. since its not a walk in the park for this can any1 tell me the step by step method on doing this. i had already downloaded the laters drivers on nvidia website. what do i do with it?

i tried using envy, but it didn't work. so i have not choice but to use the terminal.

---

### Post by coffeecat on 2007-07-27
A few comments and a couple of links for you.

Firstly, the non-proprietary 'nv' driver should give you 1280x1024 at least - even the older version that would have come with Dapper.

Secondly - don't use the drivers from the nvidia website. It's quite complicated getting that going. The packages in the Ubuntu repositories are much easier.

Thirdly - Have you thought of re-installing with the latest version, Feisty Fawn (7.04)? Installing the proprietary nvidia driver in Feisty is a simple matter of three clicks in the GUI. Oh, all right. Four. :wink:

And now to the links:

[This one]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") looks good and is from the official Ubuntu documentation. Scroll down to '6.10 and earlier'.

[And this one]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") is very good too.

**Edit:** By the way. What's a VC?

---

### Post by noof on 2007-07-27
Try the instructions at:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-1549d676e3de65ec1342cf2c8e25df0d9745b5a7](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-1549d676e3de65ec1342cf2c8e25df0d9745b5a7)

Edit: oops, coffeecat was faster :) VC = video card

---

### Post by coffeecat on 2007-07-27
> **noof said:**
> VC = video card

Thanks. :) I tried wtf from a terminal but it came up with:

> $ wtf vc
Gee...  I don't know what vc means...Hint: If you've not come across the very useful terminal utility, wtf, (no, I'm not swearing :D ), install bsdgames from the repository. Then you can look up all sorts of acronyms, e.g.:

> $ wtf ianal
IANAL: I am not a lawyerI'll leave you to try 'wtf wtf'. :wink:

---

### Post by Solidad on 2007-07-27
thanks.

---

### Post by Solidad on 2007-07-28
i just sucessfully installed, the nvidia drivers but. unfortunately i only get 1024x768 resolution as a max option. and a 60Hz refresh rate? any other suggestions?

---

