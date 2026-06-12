---
title: "Dial up with ubuntu"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Tanner31593 on 2006-10-22
Ok everyone,

heres the very shortened story,

My isp is aol,
 

I need to be able to connect with the internet.







One question,

If i just used any old dialer instead of aol,
and just used gaim to i.m,
Would it cost money on my phone bill or anything like that???






And also,

When i try to install wine it says Error: Dependency is not satisfiable: libartssc0"


Keep in mind i have NO internet connection with ubuntu, but i have aol with windows (the ppl at the last forum didnt remember that)



OK SO BOTTOM LINE,


I NEED TO CONNECT TO THE INTERNET,

if its not using aol then it has to be free........






Ive posted this in many forums but nothing.........










Tanner.






oh and i have ubuntu 6.06

---

### Post by CupofDice on 2006-10-22
I am guessing this, but I am pretty sure you have to pay for dial up (if that is what you are talking about). There is no way to do it without going with some sort of isp. Have you checked out pengaol?
[http://yolinux.com/TUTORIALS/LinuxTutorialAOL.html]("http://yolinux.com/TUTORIALS/LinuxTutorialAOL.html")
Also aol is different from other dial up isps which is why you need pengaol. I just came from aol not too long ago which is why I know wayyy too much on how to situation is screwed up ;) . They don't use generic ppp or something like that. Also linspire has a aol dialer.
[http://www.linspire.com/lindows_products_details.php?package_name=los-aol&pg=specs]("http://www.linspire.com/lindows_products_details.php?package_name=los-aol&pg=specs"), but I think you have to sign up with them (which is free). I am going to see if I can install it. 

Alright, that didn't work exactly as planned. You need linspire/cnr for it to work.

---

### Post by Tanner31593 on 2006-10-22
OK,

so is pengaol a whole separate isp than regular aol?

So with pengaol i would get a whole separate bill?


If thats true,
then i guess ill stick with aol for windows :'(,

Well,
this may be a stupid question,
but could i run aol with wine???????

---

### Post by halitech on 2006-10-22
PengAOL is simply a Linux replacement for the AOL software.

I've heard people have tried using WINE to run AOL but haven't anyone having success with it.

---

### Post by Tanner31593 on 2006-10-22
So,

would it cost me extra to use pengaol or would it just be like using my existing aol account?

---

### Post by kewldude606 on 2006-10-22
Just like keeping your current account.

---

### Post by Tanner31593 on 2006-10-22
***_Can anyone help me with my problem installing wine?????_***

---

### Post by skymt on 2006-10-22
Don't use Wine, use PengAOL. It would be much, much simpler (though still rather complex). Follow the tutorial [here](http://yolinux.com/TUTORIALS/LinuxTutorialAOL.html) (also linked to earlier in this thread). Before running any of the terminal commands in the tutorial, run this one:```
sudo -i
```Why do you need to use AOL, anyway? You can get another dial-up ISP for less money, and without the need for Wine, PengAOL, or any other mediocre workarounds. I don't use dial-up, but [PeoplePC](http://peoplepc.com/) looks good at only $10.95/month. Or, you can upgrade to high-speed Internet access. [DSLExtreme](http://www.dslextreme.com/) has DSL for $14.95/month for a year. There's very little reason to use AOL anymore.

---

### Post by CupofDice on 2006-10-23
You can install wine? Do you have another connection? Do you have a winmodem? Did ubuntu recognize it or you external modem? Have you made sure you even have the drivers for it? If not then pengaol is pointless because your modem will not work. I am on cable, but decided to get the drivers for my connexnant (wrong spelling no doubt) winmodem just in case, and luckily the process was pretty easy (their support was great=auto recognition), but that is probably because I have a connection in the first place. If those questions above freak you out then you definitely need to do more research. 

[https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html#modems]("https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html#modems")
You can download scanmodem.gz in windows and take it to ubuntu of course by fat32 or cd/usb. It will figure out what winmodem you have. I may be able to help (though I have only done this once).

---

### Post by Tanner31593 on 2006-10-24
Well,  i use aol because im not 18 and its what my parents pay for, and my mom has a jewlerey biz so she just has to have her same email adress that she made like 5 years ago cuz its on like 5000 of her business cards,

and out her aol and netzero is the only internet we can get!
we cant even get dsl cuz we live too far away,
so dial up is it, but believe me, we are #1 on the waiting list when dsl comes (mid 2007 maybe), one of the downsides of having a house in the middle of the woods, but its great.

anyway,

i want to have wine so that i can install other programs not pengaol,
and i have wine downloaded(from another computer) and when i try to install it i get Error: Dependency is not satisfiable: libartssc0" and yeah that sucks, alot.

And ive been told i need to download a repository or something,
but i cant download with ubuntu until i get pengaol installed (i will shortly)

---

