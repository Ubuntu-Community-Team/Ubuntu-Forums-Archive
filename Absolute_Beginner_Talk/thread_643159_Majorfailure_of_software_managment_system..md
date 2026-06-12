---
title: "Majorfailure of software managment system."
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by dwilson08 on 2007-12-17
Eep, I think I broke something. Everything was working fine and dandy last night, but today when I go to Add/Remove software, it tells me that I have a major software management failure and tells me to try synaptic... however when I open that it tells me
```
E: Type '“deb' is not known on line 68 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```
whatever that means. Any help would be appreciated. Thanks. (I'm not sure where the repository dialog is...)

---

### Post by dwilson08 on 2007-12-17
Yikes, after a reboot I am even further away. I now currently dont have a window manager or something, awn isn't loading, I can't switch workspaces... I still can't access my add programs ... program. This occured shortly after installing Emerald... could that have anything to do with it? (Although while trying to install a theme, it actually did absolutely nothing when I clicked on it...)

---

### Post by svalding on 2007-12-17
Sounds like a corrupt sources.list file. Do you have a livecd laying about? If you do, throw that in and see if you can't get synaptic or add/remove programs to start properly. If it does, copy the sources.list file from the live cd's /etc/apt/sources.list onto your harddrive at /etc/apt/sources.list. It is always a good idea to rename the old one to sources.old just in case you need to revert to the old copy again.

---

### Post by scopo on 2007-12-17
I am a beginner too, but I think that could be solved by becoming root, and then going to...
**/etc/apt/sources.list**
and then editing it so that line number 68 is fixed,
My _beginners_ guess is that part of that line has been deleated somehow leaving just a deb command which on its own dosent make any sense - so if you delete the rest of the line it should fix it.
But check with someone who know what they are talking about before you do anything !!!:)

---

### Post by dwilson08 on 2007-12-17
Okay thanks I'll try that. Strangely enough... now window switching is working... so is emerald... so is AWN... but that file is still screwed up.

---

### Post by dwilson08 on 2007-12-17
Thanks scopo, that worked. For some unknown reason line 68 & 69 had apostrophes before and after the deb entry thing... when I deleted the apostrophes (it was around 2 screenlet things) it now works.

Thanks for the quick replies you guys!

Problem solved.

---

### Post by christhemonkey on 2007-12-17
EDIT: I type too slowly, problem already solved.

You need to edit the file /etc/apt/sources.list using a command like this:
```
sudo nano /etc/apt/sources.list 
```
Then find line 68 and at the start of that line there is an extra:```
 &#8220; 
```
Delete this and then run this:
```
sudo apt-get update 
```

Then you should be back on track!

---

### Post by lamalex on 2007-12-17
> **svalding said:**
> Sounds like a corrupt sources.list file. Do you have a livecd laying about? If you do, throw that in and see if you can't get synaptic or add/remove programs to start properly. If it does, copy the sources.list file from the live cd's /etc/apt/sources.list onto your harddrive at /etc/apt/sources.list. It is always a good idea to rename the old one to sources.old just in case you need to revert to the old copy again.
^^This is one way to do it, although you'll lose any custom repos you have entered

The better way to do it is this, at login chose "failsafe terminal". This will give you just a shell. Next do
```

sudo vi /etc/apt/sources.list
:68

```
notice the ':' that's important for commands in vi, now look at the line, it looks you have a quote or something mixed in there. it should just look like this
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universeYou probably have a different URL for the repo, look around in there for quotes too or any special characters that don't belong. move your cursor to them and hit x to delete (no : ).
Now save and quit ```
:wq
``` and logout control+alt+backspace. Now log back into gnome and apt should be fixed.

EDIT: Yikes, I'm really slow. vim is fast to use, slow to explain!

---

