---
title: "That Damn Blinking Cursor!!!"
date: 2011-10-10
forum: Apple Hardware Users
---

### Post by NerdSauce on 2011-10-10
Ok, so I decided to dual-boot my 27" iMac (Core 2 Duo) with the latest Ubuntu release (v11.04). I burned the .iso onto a DVD, partitioned my hard drive using Boot Camp and installed rEFIt.

Then I reinserted the Ubuntu disc, rebooted and have had problems ever since. Every time I turn off then turn on my Mac I get the white screen which I hold down the Option key. The screen then goes black, has a blinking white cursor which then gives way to a purple screen with some graphic at the bottom that looks like a window a dash and some stick figure....

Then the screen goes black and I hear the DVD whirring and clicking but the screen remains black and nothing else happens (except the DVD revving up occasionally). I did manage ONCE to get to the "Try Ubuntu without Installing" options menu, which I clicked and then chose English as the language. But after that it returned to a black screen with the DVD whirring. I think I heard the Ubuntu start-up sound - but that did me no good when my screen remained blank.

Now I can't even get that menu to re-appear, and I can't seem to get the Mac OS to boot up now either. I just keep getting the white screen and if I remove the Ubuntu disc and do nothing it goes to the black screen with white blinking cursor and remains there permanently. This is really starting to **** me off as although I did back up everything from my Mac - it does me no good if the damn OS won't even boot up! And no, I don't have the original Mac install disc any longer. 

Where am I going wrong and how can I fix this?! Please help!!! :confused:

---

### Post by drs305 on 2011-10-10
From what I read, you never were able to install Ubuntu.

If you are able to get the DVD menu to appear, try pressing the F6 key to allow you to add boot options. Select 'nomodeset', which may allow you to see the Desktop.

Here is more detail about boot options:
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

---

### Post by NerdSauce on 2011-10-10
You are indeed right that I hadn't yet been able to actually install Ubuntu ...
...but, thanks to your advice I managed to switch to 'nomodeset' and at least now I actually see the words 'Ubuntu 11.04' and the four blinking white-to-orange dots on the screen!

Perhaps now I can actually install the damn OS! lol
Will keep you updated on my progress....Thanks!

**Edit:** *During the Ubuntu loading screen some orange text appeared saying something was not valid and it was aborting??? I couldn't quite catch exactly what it said because it vanished too quickly. Will try again and see if the same thing appears.*

---

### Post by drs305 on 2011-10-10
While I'm encouraged by your partial success, I don't know enough about Apple integration to suggest what might be wrong.

I will note that there are other F6 options which you can also select (you can have more than one). Perhaps another option is required. Hopefully someone with Apple experience will visit your thread.

---

### Post by NerdSauce on 2011-10-11
Ok, unfortunately it seems my problems are going to be terminal. Something to do with graphic driver issues and I'm not an advanced enough user to mess around with command lines and the such.
I could get it to the Ubuntu loading screen with the white-to-orange dots - but every time without fail it would start doing checks (like battery level etc) and then this message would appear:
***Stopping system vrun level compatability**  (there may have been more to it than this, but it always vanishes too fast for me to read it all the way through)*


Oh, I finally worked out why I wasn't getting the option to go back to my Mac OS - I was holding down the wrong button during boot-up!! d'oh! 
I think I'm just going to delete the partition I made and give up trying to dual-boot my Mac for now - at least until I can get someone out to help that knows what they're doing!

Thanks so much for the help anyways - it's much appreciated! :D

---

