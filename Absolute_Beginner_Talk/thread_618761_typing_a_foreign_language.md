---
title: "typing a foreign language"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by crazydiver on 2007-11-20
how do you type in a foreign language such as Japanese, chinese, and korean?

---

### Post by miyuki on 2007-11-20
> **inversekinetix said:**
> In case you can't get on IRC, here are my settings

system>>>administration>>>language support

  #English and Japanese are checked
  #Enable support to enter complex characters is also checked.


system>>>administration>>>>> synaptic package manager

  #scim is installed


system>>>preferences>>>>scim input method setup

  # IM ENGINE >>> Global Setup >>> Japanese is checked


everything else is default.

I have a feeling that after I installed the language pack for japanese it didnt work, then I enabled it in the SCIM manager and it did.  Don't quote me on that though, I can't remember half the things I've done setting up this new OS.

you would need to do the same thing for Korean and Chinese. To actually use it, you would need to...

> To use that thing (scim) in a word processor, you need to right click the mouse, go to input methods or something and then u select SCIM input method rather than whatever that's already selected as default. When that is done, you can now click on scim icon and change languages =].

the only problem for me using scim is that it won't type foreign languages in search boxes or forums...just word processors and e-mail textbox only.

---

### Post by crazydiver on 2007-11-20
thank you... 

I remember back with Feisty, all I had to do was shift+spacebar and I was already on my way to write in Korean.

Everything you told me was a step ahead than before and everything was all set!!! The only problem is where do I go to select which font I want to use? 

I guess I'm so used to Feisty because it was really easy... just click shift and spacebar... now it looks like its a whole new level. Where do I go to choose the font I want to use??? thank you!

Thanks!

---

### Post by miyuki on 2007-11-20
your welcome. 
I agree, I think Feisty is so much easier. Didn't take me long enough to figure out how to type in foreign languages. This version is so confusing. I'm still trying to get help with figuring out how to input other languages everywhere, not just in word processors :sad: 
if you ever figure out how to do so before i do, please share it with me T^T thnx

btw, regarding the font, i really have no clue...i'm just happy that i can type in other languages right now lol

---

### Post by yureia on 2007-11-22
Hello miyuki,
how did you type in other languages in internet browser?
I'm using firefox, and I do not see the menu for changing to SCIM input language when writing an e-mail, unlike word processor.
My SCIM setup has Japanese and Korean enabled, but the hotkeys for changing to those languages don't work anymore after upgrading to Gutsy..they worked in any application in Feisty.
I'm rebooting to Windows XP, and using IE just to type in Korean or Japanese. Go dual OS! ..but a pain in the..

---

### Post by nuir on 2007-11-23
The program you use to type foreign languages is called SCIM, for some reason in Feisty it was easier to make it work... anyway, here's a link to the official guide for SCIM, that's what I did to set it up properly in my own system, I hope you find it useful.

[https://help.ubuntu.com/community/SCIM]("https://help.ubuntu.com/community/SCIM")

---

### Post by yureia on 2007-11-25
Thank you for your comment nuir.
The thing is, it still doesn't change language in another application other than gedit, and Firefox haven't had 'input method' menu at all.
In English(CA) session under Feisty, SCIM could effect Firefox input area(like typing in any ID and password, this forum, searchbox, etc..).
My shortcut(assigned in Feisty) for changing to Japanese was alt+J, and that one doesn't do anything any more, although that key's still enabled under the SCIM setup.
Wonder what changed about SCIM between Feisty and Gutsy?

---

### Post by miyuki on 2007-11-25
> **nuir said:**
> The program you use to type foreign languages is called SCIM, for some reason in Feisty it was easier to make it work... anyway, here's a link to the official guide for SCIM, that's what I did to set it up properly in my own system, I hope you find it useful.

[https://help.ubuntu.com/community/SCIM]("https://help.ubuntu.com/community/SCIM")

THANK YOU VERY MUCH FOR THAT LINK, nuir =D 
now SCIM works for everything :D I now can type in Chinese &#20013;&#25991;, Japanese &#12395;&#12411;&#12435;&#12372;, and English! YAY~

but i have a question, it says...
> Save the file, then to be sure you won't be affected by previous configurations you can delete the folders .scim and .xinput in your home directory. Since they are hidden folder, you can make them appear in Nautilus with the shortcut Ctrl+H.
i didn't delete the folder since i only had .scim folder, which had files in there, would it be a problem not deleting it??

---

### Post by nuir on 2007-11-27
> **yureia said:**
> Thank you for your comment nuir.
Wonder what changed about SCIM between Feisty and Gutsy?

I'd like to know too, anyways, the guide worked for me really fine, so I'm not sure what's the exact issue in your case :( the shortcut in my computer is ctrl+space and it changes back and forth from the last input I enabled. I actually have many different langauges and I can use them in any program, be it firefox, terminal or whatever.

I found this thread [_here_]("http://ubuntuforums.org/showthread.php?t=600183&highlight=scim"), maybe you can find some useful info there.

Good luck!

---

### Post by nuir on 2007-11-27
> **miyuki said:**
> 

i didn't delete the folder since i only had .scim folder, which had files in there, would it be a problem not deleting it??

well... since SCIM is already working for you, then it'll probably be just be fine ;)
if you find some bugs later you could try deleting them, but I don't think it's too important. (of course, I'm nor an expert, but it didn't make much of a difference for me either)

---

