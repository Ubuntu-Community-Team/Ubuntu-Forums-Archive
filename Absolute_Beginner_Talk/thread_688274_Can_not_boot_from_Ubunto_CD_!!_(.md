---
title: "Can not boot from Ubunto CD !! :("
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by quecoder on 2008-02-05
Hello guys ,
I'm trying to install Ubunto from it's original CD sent from Ubunto themselves , thus , a high quality CD , but getting this VERY VERY annoying problem ( again for 10th time after trying to burn by myself) "
"**media test failure, check cable error"** .. 
My lap top is : Toshiba Satellite A100 !! 
Please guys please help me I want this OS badly !!

---

### Post by emarkd on 2008-02-05
That sounds like a hardware error to me.  Can you boot from or read other CD's?

---

### Post by quecoder on 2008-02-05
Thanks emark for your quick reply , 
I can use my lap top recovery CD very well , to recover my windows ..I have also burned a CD yesterday successful for ubutno but got the same error when trying to boot from it ..

---

### Post by quecoder on 2008-02-05
I even try to open the live CD on windows to explore it , but can not !
But I can read DVDs I burned last months ago and CDs , yes !! but Booting is always fail for any unix distro and even , as I mentioned , can not play the CD on windows for this specific ubunto CD sent from ubunto besides not being able to boot from it

---

### Post by emarkd on 2008-02-05
Not sure if this will help, but [here's]("http://www.computerhope.com/issues/ch000706.htm") a troubleshooting guide I found through Google that may be relevant.  It basically says it's a BIOS configuration error.

---

### Post by quecoder on 2008-02-05
emark , yes I have read this site before asking , tried to reset the bios but no thing new happend ... very annoying

---

### Post by Church.Cameron on 2008-02-05
Make sure you hardware specs are up to Linux standards there is hardware that will attempt to use linux but will only fail. the problem sounds like a hardware problem. from what was said before. Check in to that if the problem continues.

---

### Post by rkd on 2008-02-05
At least one person was able to bring up Ubuntu 7.10 on the Satellite A100 without trouble, so unless your hardware is broken, it ought to work.

I suppose there is some chance that the disc you received is defective, even though it came from Ubuntu. However, I'm confused by your reference to burning something for the 10th time.  So let me ask a few questions to be sure I understand what you are doing and what is going wrong. Fill in any additional details as you see fit.

Are you booting from the CD that Ubuntu sent you?

Exactly which version of Ubuntu is it?  Ubuntu, Kubuntu, Xubuntu, etc.?  7.04 (Feisty) or 7.10 (Gutsy)?

Are you getting the media test failure when booting that CD?  If so, at what point in the boot does it occur (what have you seen on the screen before the error message)?

What did you try to burn 10 times?

One simple test you could do is take the disc and boot it on another computer. If you don't have another computer, perhaps a friend or member of your family has one you could use.  Remember, booting the Live CD won't change anything on their computer (unless you tell it to install), so it should be quite safe to test.  You could just let it boot to the desktop, but it might be better to choose the boot option that tests the disc -- just use the down arrow to go down to the option that says that.

I'm sure once we get you past this problem, you'll be able to get Ubuntu running on your computer.  This guy seems to have installed Ubuntu on the A100 with very little problems:

[http://www.pierocampanelli.info/hack/2008/01/08/ubuntu-gutsy-71-on-a-toshiba-satellite-a100-022/](http://www.pierocampanelli.info/hack/2008/01/08/ubuntu-gutsy-71-on-a-toshiba-satellite-a100-022/)

---

### Post by wheredidrealitygo on 2008-02-05
I had that exact same laptop a while ago, that was before Gutsy (7.10) came out, I would recommend installing Feisty (7.04) which never gave me any problems, from there you can just upgrade.

---

### Post by quecoder on 2008-02-05
> **rkd said:**
> At least one person was able to bring up Ubuntu 7.10 on the Satellite A100 without trouble, so unless your hardware is broken, it ought to work.

I suppose there is some chance that the disc you received is defective, even though it came from Ubuntu. However, I'm confused by your reference to burning something for the 10th time.  So let me ask a few questions to be sure I understand what you are doing and what is going wrong. Fill in any additional details as you see fit.

Are you booting from the CD that Ubuntu sent you?

Exactly which version of Ubuntu is it?  Ubuntu, Kubuntu, Xubuntu, etc.?  7.04 (Feisty) or 7.10 (Gutsy)?

Are you getting the media test failure when booting that CD?  If so, at what point in the boot does it occur (what have you seen on the screen before the error message)?

What did you try to burn 10 times?

One simple test you could do is take the disc and boot it on another computer. If you don't have another computer, perhaps a friend or member of your family has one you could use.  Remember, booting the Live CD won't change anything on their computer (unless you tell it to install), so it should be quite safe to test.  You could just let it boot to the desktop, but it might be better to choose the boot option that tests the disc -- just use the down arrow to go down to the option that says that.

I'm sure once we get you past this problem, you'll be able to get Ubuntu running on your computer.  This guy seems to have installed Ubuntu on the A100 with very little problems:

[http://www.pierocampanelli.info/hack/2008/01/08/ubuntu-gutsy-71-on-a-toshiba-satellite-a100-022/](http://www.pierocampanelli.info/hack/2008/01/08/ubuntu-gutsy-71-on-a-toshiba-satellite-a100-022/)


Are you booting from the CD that Ubuntu sent you?
- yes ,  "Ubunto 7.10 for your PC " is the label. just received it by mail ,  inserted it into the CD rom , restarted the system and chose boot from CD ..

Exactly which version of Ubuntu is it?  Ubuntu, Kubuntu, Xubuntu, etc.?  7.04 (Feisty) or 7.10 (Gutsy)?
- it's 7.10 , I think it's Gusty , too new to unix systems to know that.

Are you getting the media test failure when booting that CD?  If so, at what point in the boot does it occur (what have you seen on the screen before the error message)?
 - just after choosing to boot from CD  , the screen go blank ( black of course ) and error appears then windows starts.

What did you try to burn 10 times?
 - because every time I encounter this error , I felt this is because of a wrong way in burning till I reach the tenth trial with no hope , decided to get a CD from ubunto instead  that is already burned..

additional info  : some times I fail in burning CDs ( I think they are of bad quality  ,some of them cost me only 30 cents .. :) .. I also hear a strange sound when the CD is running .. like "clak clikkk tikk" :)

I'm afraid that this is a defect in my hardware  , thought , I can , as mentioned , boot from the recovery CD shipped with my lap top..

for trying it on another PC , I don't expect this can happen in the next few days ..

---

### Post by rkd on 2008-02-05
Okay, that makes things a little more clear.

Do I understand correctly that when you boot from the Ubuntu CD, you get the media test failure before seeing the Ubuntu boot menu that asks whether you want to boot or install Ubuntu, boot in safe graphics mode, etc.?  Or do you see that boot menu and the error appears after you choose which boot option you want?

My guess is that you get the message before seeing the boot menu. If that is true, it sure sounds to me that either the Ubuntu CD is defective or your CD drive is defective.  Since you can boot other CDs okay, I think that makes it more likely that the Ubuntu CD is defective.

What would you like to do: Wait until you have a chance to try booting the Ubuntu CD on another PC, or try again to burn your own CD?

---

### Post by quecoder on 2008-02-05
Yes , as you said , I'm getting the error before the menu , just after choosing to boot from the CD instantly  ... I'll try as you said in the next few days ..  :'( as I don't have access now to another PC

---

### Post by rkd on 2008-02-05
Okay. When you get back to working on this, post to this thread again and we'll get notified of the new post.

I don't know whether this is possible, but if when you get to try the CD Ubuntu sent you on another PC, what will you do if it also fails there?  Would it be possible to take with you a blank CD or two and if your current CD proves bad, download and burn your own Ubuntu CD on that PC? If you do, remember to select a slow speed and use the command for burning an image file, not the one to make a data CD.

---

### Post by quecoder on 2008-02-06
rkd  , thank you for helping . 
yes , I will try to boot from another PC and when it returns this error again , i will burn another one ..will keep u updated ..thx :)

---

### Post by bwtranch on 2008-02-06
Still confused on why you need to burn anything. If you got the CD from Caniocal (comical) I don't understand. You just put it in your drive and set your BIOS to boot from a CD. If you are trying to burn it, you won't get very far. Ha

---

### Post by BruisedQuasar07 on 2008-02-06
This may sound goofy but I learned a long time ago to always clean any 
CD before I try to use it. Use plastic eye glass spray cleaner and a micro fiber
cloth, use single direction, straight out from the CD hole to the edge movements.

I have recommended this to several people who complained about odd
error messages and failure to work when they tried to use a particular
CD, including professionally burned Linux live cd distros. So far, all of them
were immediately able to use their CD (or DVD movie)

--Bruised

---

### Post by Michl on 2008-02-06
A stab in the dark:  make sure the cd is in the drive before BIOS loads.

---

