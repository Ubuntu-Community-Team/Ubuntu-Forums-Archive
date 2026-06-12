---
title: "Which version should I use?"
date: 2009-08-16
forum: Apple Hardware Users
---

### Post by ana09 on 2009-08-16
Hi, 

I'm a newcomer in ubuntu and I already install Ubuntu 8.10 on a MacBook. But I need g77 to compile a program that I need. It seems to be imposible to get it for Intrepid. 
Perhaps should be better Gutsy? Will it works good on MB?

I'm happy with Intrepid, all looks ok, except my modem it's need connection but without configure it there is no internet, so... :(
Only one thing for the moment,  keyboard, it doesn't work exactly.
Bloq. Uppercase doesn't highlight (but that is not a really problem, I think).

Could anyone help me?


Thanks, Ana

---

### Post by wojox on 2009-08-16
Compiler:
[https://launchpad.net/ubuntu/intrepid/+package/g77-3.4](https://launchpad.net/ubuntu/intrepid/+package/g77-3.4)

Modem:
[https://help.ubuntu.com/community/DialupModemHowto/Modems](https://help.ubuntu.com/community/DialupModemHowto/Modems)

Don't know about uppercase highlighting?

Hope that helps.

---

### Post by rifak on 2009-08-17
sudo apt-get install g77 doesnt give you the option to install? and may i suggest installing the newer gnu fortran compiler, gfortran?

well, i have a black macbook, and 8.04 works great with it. heres the link: [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

after all updates are installed (youll need a wired connection) and a restart, wireless works

---

### Post by ana09 on 2009-08-17
Thanks for links, 
I'm going to download gcc, hope it works. Should I download all?
.dsc, orig and .diff.

About Uppercase, in my keyboard light after you press to block uppercase button doesn't ignite. I configured keyboard in different ways but never it light.

My airport works ok with Intrepid.

Perhaps Hardy should be a better option, but I'll give a chance to intrepid for a while.

(Thanks for answer)

Best regards, Ana

---

### Post by ana09 on 2009-08-17
Hi, I'm again.
I used synaptics to get gcc-.... Tried to compile my program and failed (error f9.. or something like that), then installed gfortran with synaptics, now the program run but
compiler doesn't undertand fortran 77, and says there are mistakes,  a lot of, but I now there aren't. This program is running in other computers.
What can I do??
Please help!!

---

