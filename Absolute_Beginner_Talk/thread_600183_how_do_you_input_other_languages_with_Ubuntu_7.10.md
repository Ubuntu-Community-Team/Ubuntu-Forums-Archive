---
title: "how do you input other languages with Ubuntu 7.10?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by miyuki on 2007-11-02
Hi, I'm having a lot of problems with how to input other languages on Ubuntu version 7.10. I did it before with version 7.04, but I can't seem to make it work with this new upgraded version. I'm really frustrated! I really need help!!! Can someone help me plz???
In addition, when I go to "Language Support" and it opens up, there's a window that pops up saying that there are some files that I didn't finish downloading. However, those files are non-authentic. What does that mean?? So, is it necessary to download those files??? I'm quite confused. Could someone help me plz!!!!!!!!!!!!!!

---

### Post by mikewhatever on 2007-11-02
Please calm down. Can you tell in unemotional english what happens when you add language support? What exactly does not work?
To try and solve the authentication issue, run
> sudo aptitude update

---

### Post by miyuki on 2007-11-07
Thank you for replying, but what is sudo aptitude update??? Just so you know, I'm not really good with computers, especially with those codes and commands and so on.

So, here's my problem in unemotional English. I want to be able to input Chinese & Japanese on my laptop, however I can't do that with Ubuntu7.10; which I was able to do so with Ubuntu7.04. I used to enter other languages by clicking on the little keyboard icon on the top right corner of the top panel, and it gives me different language input options. (I think that keyboard icon is for SCIM...) However, with U7.10 for some reason I can no longer do that. I still see the SCIM icon (keyboard icon), yet it doesn't give any options, in fact, I can't even click on it. I did install both Japanese & Chinese in "Language Support" and both languages are enabled in SCIM setup. So, I really don't know why I can't input other languages anymore, and I really need help with making that work.

I hope this time it's much clearer and understandable. Sorry if I wasn't clear with my 1st post because I was really frustrated.

---

### Post by inversekinetix on 2007-11-07
Konnichi ha,

did you try the hotkey ctrl + spacebar? it changes the language input.

---

### Post by NotTheMessiah on 2007-11-07
> **inversekinetix said:**
> Konnichi ha,

did you try the hotkey ctrl + spacebar? it changes the language input.

Inversekinetix : i notice you have the 640GTS...how do you feel about the new cheaper 8800GT:)

---

### Post by miyuki on 2007-11-07
i tried that...but it doesn't work for me T^T
i hate this...it's really frustrating

---

### Post by inversekinetix on 2007-11-07
Im at work now miyuki, when i get home Ill have a look on my ubuntu box and see if i can help.  Dont worry i dont think it should be hard to do, I managed it on my box. Have look in your language settings manager and make sure the languages you want are enabled and not just installed.

---

### Post by NotTheMessiah on 2007-11-07
did you try system/admin/ language support -- and then select chinese

---

### Post by miyuki on 2007-11-07
yes i did that, i checked off Chinese, Japanese, and English (of course); and I also check the box for 'input method' (enable support to enter complex characters)
as for SCIM setup/IMEngine/Global Setup, i checked off (enabled) all 3 languages.

---

### Post by inversekinetix on 2007-11-07
> **NotTheMessiah said:**
> Inversekinetix : i notice you have the 640GTS...how do you feel about the new cheaper 8800GT:)



It looks really good, out of the box it looks a little better than GTS, but Ive had this for GTS since febuary and its been great, a good overclocker and the memory bus bandwidth is better than the new one.

The new one is built on 65nano technology and fits into a single slot, I think there are going to be some heat issues with it when overclocking, but it does look tasty.  From what I've seen so far, and cooling isnt a problem, it is a contender for going into my new SLI gaming rig,  slap 2 of them in with a new cpu and better ram.

It always sucks when new things come out cheaper than what you paid a lot for, but you have to pay the price when its new.

---

### Post by inversekinetix on 2007-11-07
Sorry miyuki, I didn't get home from work until very late yesterday, did you get your problem fixed?

---

### Post by miyuki on 2007-11-07
nope, the problem is not fixed, and i'm still stuck inputing only English. *sigh*

---

### Post by inversekinetix on 2007-11-08
I have another late finish tonight by the looks of it. Did you try asking for help in the IRC channel?  you will probably get a much quicker response.  I wish I knew linux well enough to try and help without being infront of the machine but unfortunately I'm new too.  If I have any life in me when I get home and if I switch on the PC i will try and have a look.  You'll get it fixed soon enough, try the irc for now.

---

### Post by inversekinetix on 2007-11-08
hi miyuki are you there?  I managed to get back early,  I can be on the ubuntu IRC for the next hour if you still need help.

---

### Post by inversekinetix on 2007-11-08
In case you can't get on IRC, here are my settings

system>>>administration>>>language support

  #English and Japanese are checked
  #Enable support to enter complex characters is also checked.



system>>>administration>>>>> synaptic package manager

  #scim is installed



system>>>preferences>>>>scim input method setup

  # IM ENGINE >>> Global Setup >>> Japanese is checked




everything else is default.

I have a feeling that after I installed the language pack for japanese it didnt work, then I enabled it in the SCIM manager and it did.  Don't quote me on that though, I can't remember half the things I've done setting up this new OS.

---

### Post by miyuki on 2007-11-09
OMG, I finally got it working. I feel so stupid now, it was so simple.](*,):oops:
however, it only works with text programs and msn. I can't type other languages in search engines or here. weird....

inversekinetix: Thank you very much for taking the time to help me fix my problem. I really appreciate your help. :D

---

### Post by inversekinetix on 2007-11-09
> **miyuki said:**
> OMG, I finally got it working. I feel so stupid now, it was so simple.](*,):oops:
however, it only works with text programs and msn. I can't type other languages in search engines or here. weird....

inversekinetix: Thank you very much for taking the time to help me fix my problem. I really appreciate your help. :D


you're welcome, glad it'S working.  I'll check mine to see if it works in other programs.  have fun.
:popcorn:

---

### Post by gglbr on 2007-11-19
hey, miyuki. 

how did you solve the problem at last?
I have exactly the same question and yet have not figured out.

I followed all the steps: enable language support, enable complex input, install scim, setup scim. yet still nothing happens when I hit ctrl+space.:confused:

---

### Post by miyuki on 2007-11-20
> **gglbr said:**
> hey, miyuki. 

how did you solve the problem at last?
I have exactly the same question and yet have not figured out.

I followed all the steps: enable language support, enable complex input, install scim, setup scim. yet still nothing happens when I hit ctrl+space.:confused:

hi there. =]

I did somehow manage to get scim working, but it only works in word processors and e-mail text box. I still  can't type anything other than english in search boxes or here (forum postings). 

To use that thing (scim) in a word processor, you need to right click the mouse, go to input methods or something and then u select SCIM input method rather than whatever that's already selected as default. When that is done, you can now click on scim icon and change languages =]. 

I hope my explanation is clear enough for you to follow, since i'm not very good at explaining things =P. However, as I was saying, it only worked for me in word processors and e-mail textboxes. If you want to search in another language, i guess, you'd have to copy and paste it off the word processor o.O at least that's what i'm doing....very annoying >.> (i hope that can be fixed soon....o.O)

---

### Post by inversekinetix on 2007-11-20
Hi Miyuki, try in the SCIM settings manager

GLOBAL SETUP

uncheck the 

"share same input method between all applications"

that should allow you to use the language in everything

---

### Post by miyuki on 2007-11-20
> **inversekinetix said:**
> Hi Miyuki, try in the SCIM settings manager

GLOBAL SETUP

uncheck the 

"share same input method between all applications"

that should allow you to use the language in everything

ah, thank you, but i tried to do that and it didn't work *sigh*

---

### Post by randomZ on 2007-11-25
By the looks of it, I'm also suffering from the same problem. I had SCIM working perfectly before upgrading from 7.04 to 7.10, at which point SCIM stopped working completely. So I removed it and installed it freshly according to the [guide]("https://help.ubuntu.com/community/SCIM?highlight=%28scim%29") in the wiki.

Now I have a SCIM icon in the bar on the top of the screen. I seem to be able to input Japanese characters in pure GTK applications like GEdit by right-clicking and selecting Input Methods / SCIM. However, it doesn't work in other applications like OpenOffice and Firefox.

Is this a problem with the upgrade process that might be solved with a fresh installation (as I'm now considering to do)? Or did anyone get this problem with a fresh Ubuntu installation?

---

### Post by miyuki on 2007-11-26
I'm really glad to say that my problem with SCIM is now officially solved. Thank you everyone who helped me =D. Now I can type foreign languages in any program, FINALLY!!!! =D

randomZ: try following the steps from the following link, that's where i got the instructions to how to fix things up completely. phew~

> **nuir said:**
> The program you use to type foreign languages is called SCIM, for some reason in Feisty it was easier to make it work... anyway, here's a link to the official guide for SCIM, that's what I did to set it up properly in my own system, I hope you find it useful.

[https://help.ubuntu.com/community/SCIM]("https://help.ubuntu.com/community/SCIM")

---

### Post by randomZ on 2007-11-26
That's the guide I was using, and I'm sad to say it didn't work completely. I can use SCIM in pure GTK applications like gedit, but not in other applications like Firefox and OpenOffice.

Any suggestions what I might have done wrong? What mistakes did you make before you got it working, miyuki?

---

### Post by miyuki on 2007-11-26
ah...i'm really sorry to say that i'm not sure where you've gone wrong, but double check if you did the following steps first...
> 
system>>>administration>>>language support

#English and Japanese are checked
#Enable support to enter complex characters is also checked.


system>>>administration>>>>> synaptic package manager

#scim is installed


system>>>preferences>>>>scim input method setup

# IM ENGINE >>> Global Setup >>> Japanese is checked


everything else is default.

also uncheck "share same input method between all applications" in Global Setup of SCIM settings manager.

These steps should allow you to input different languages in instant messengers and open office (at least...that's what happened to me)

Then you can follow the guide from that link...instead of changing the lines "something something=xim" to ...="scim-bridge" try change it to ...="scim" maybe that'll work, well...it worked for me.

I really hope that yours will work too, i know how frustrating it is when it's not working >.<

---

### Post by Matthew Bartram on 2007-11-26
Did you follow the "Additional configuration if you're not using a CJK session" section as well? I had the same problem - it seems unless you're logged in a session in Chinese, Japanese or Korean, then you need to set up the "scim-bridge", as described in that section.

---

### Post by randomZ on 2007-11-26
Hi,

it seems all it needed was a complete reboot. Sorry to bother you all!

However, shortcuts for selecting a specific input method don't seem to work... is this the same for everyone? For example, I can assign a keyboard shortcut to Japanese/Anthy under Input Methods / Global Settings, but the shortcut won't work.

Sebastian

---

### Post by TWO on 2007-12-11
In spite of having followed the suggestions mentioned so far in this thread, I still can't enable Japanese support via SCIM. 

For starters, even when setting the program to appear permanently it doesn't appear. Also, not matter how many times I configure the program, an icon fails to appear in the taskbar...

I am quite stuck and I also need this Japanese support to work. It was quite fine in Feisty.

---

### Post by TWO on 2007-12-11
It appears I don't pay half enough attention to what I read.
[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

Has also solved my problem. I hadn't properly read the section which requires editing a certain file.

Glad to have Anthy working again.

My initial problem- as mentioned on that site- what that I did not have 'anthy-bridge' installed. I soon corrected that via the Synaptic Package Manager.

&#25163;&#20253;&#12387;&#12390;&#12367;&#12428;&#12390;&#12354;&#12426;&#12364;&#12392;&#12358;!

:)

---

