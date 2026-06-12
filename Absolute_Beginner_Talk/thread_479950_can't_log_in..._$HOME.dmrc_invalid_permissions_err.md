---
title: "can't log in... $HOME/.dmrc invalid permissions error"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by clitmaster on 2007-06-20
hey everyone! i'm getting the "$HOME/.dmrc file is being ignored" error. i've searched these forums and found about 10 different threads regarding this issue, i followed all the steps, but i'm still getting the same error message... ok, i'll explain wots happend so far:

i want to dual-boot windows vista and ubuntuStudio (from the one 160gb hdd)... first i installed vista on the first partition, then ubuntu 7.04 on the second partition... a third partition is fat32, for all my files, to be shared between ubuntu and vista... i wanted ubuntuStudio so i downloaded it and installed it, and at the same time i wanted to change where my fat32 partition is mounted under ubuntu...so in fstab i changed it from "/clitsShit" to "/home/clit" (the directory already exists)....

BAM, first occurance of the "$HOME/.dmrc" error when i tried logging in.... i thort it may have been something to do with ubuntuStudio/nvidia graphics...but nope, the issue was the fstab....i commented out all the drives i just changed (which was the windows partition and the fat32 /home/clit partition)...and that was it, straight into ubuntuStudio, resolved!

i downloaded the ubuntuStudio iso and made my dvd....i reinstalled ubuntuStudio, off the dvd this time, formatting the ext3 & fat32 partitions....fresh install.....
BAM!...the $home/.dmrc error is back....
and thru all this and extra "lowLatency" choice has appeared in grub..

i've tried commented out drives in the fstab file
i've tried setting the permissions (644 and 755 for both / and /home

when i type: ls -la /home/
i get: 
```

drwxr-xr-x   3 root root 4096 2007-04-12 19:11 .
drwxr-xr-x  21 root root 4096 2007-04-21 19:22 ..
drwxr-xr-x   2 root root 4096 2007-04-21 19:09 clit

```

**so i keep getting the error msg, even afta a fresh install**


so yea, sorry bout the life-story lol and if im unclear on anything let me kno....

any help is appreciated heaps! im lovin this ubuntuStudio, and i look forward to using & supporting it

---

### Post by yabbadabbadont on 2007-06-20
Try following these instructions:  [http://ubuntuforums.org/showpost.php?p=2881561&postcount=3](http://ubuntuforums.org/showpost.php?p=2881561&postcount=3)

Edit: Sorry, looks like you did search first.  :oops:

---

### Post by clitmaster on 2007-06-20
lol yea np's..i've actually been thru that also.....the first 2 commands are ok....but when i try "chmod 644 /home/clit/.dmrc" it comes back saying "chmod: cannot access '/home/clit/.dmrc': NO SUCH FILE OR DIRECTORY" 

hmm, doesn't seem to find it :s

---

### Post by yabbadabbadont on 2007-06-20
Then create it...  ;)
```
touch /home/clit/.dmrc
chmod 644 /home/clit/.dmrc

```

Edit: I almost felt dirty typing in that first command...  :lol:

---

### Post by clitmaster on 2007-06-20
haha! yea my names clinton, nickname clit.... ya get used to it

umm,, ahhh lol sorry... the commands in that link DID actually work.... i'm sure i would've done that i looked everywhere!! lol maybe it was cos i went into recovery mode, instead of atl-ctrl-F2...or cos i typed shutdown -r now instead of reboot...or maybe i didnt do it lol who knows!

anyways its fixed and working n im into my new shiny ubuntuStudio....thanx heaps yabbadabbadont lol cool name btw...i hope i can b leet sauce 1 day helping noobs n ****

2 questions that come to mind tho....

1. wot is this lowLatency choice that comes up in grub? its the top one so its used by deffault, should that matter? it seems to be working ok so far
2. i noticed since installing ubuntuStudio im missing some apps, such as gimp, and games n stuff....i thort installing ubuntuStudio installed the base of ubuntu then studio apps on top of it? how do i activate the base programs for standard ubuntu?

---

### Post by yabbadabbadont on 2007-06-20
I don't use UbuntuStudio, but the low latency option probably just boots the low latency kernel.  i.e. a kernel that has been built with low latency patches that allow for fast (near real-time) response to hardware events.  The default kernel used by Gentoo has included these patches for years.  I don't know why Ubuntu doesn't...

You should be able to simply use synaptic to install any programs that you are missing and want.  System->Administration->Synaptic Package Manger (in gnome).  Use adept in KDE to do the same.

---

### Post by clitmaster on 2007-06-20
awesome, i'll c how i go from here on out
cheers for the support ;)

---

### Post by hatchetjuggla on 2007-06-20
> **yabbadabbadont said:**
>   System->Administration->Synaptic Package Manger (in gnome).  Use adept in KDE to do the same.

Maybe I should have shown you that way before introducing you to apt-get..... :P

---

### Post by clitmaster on 2007-06-21
my girlfriend wanted ubuntu studio, so i formatted her HDD, installed windows on the first partition, ubuntuStudio and the second, and fat32 on the third.....windows was mounted to /windows, ubuntuStudio to root / , and the fat32 partition was set to mount at /home/mona, during the partition setup during the installing process......

installation was successful, but that $HOME/.dmrc error came back to haunt me!! it wouldn't let me log in....i tried all the previous troubleshooting, with permissions and ****, same thing

i thort maybe its a mounting/fstab issue....i reinstalled/reformatted ubuntuStudio again, only this time i left the mounting as defaults (/media/sda2,  /media/sda3, etc...)

worked like a charm, no $Home error at all!! :D

so yea, it seems the (or one) cause of this stupid $HOME/.dmrc error is where ur partitions are mounted (fstab).....

hope sum1 gettin the same prob finds this thread useful ;)

---

### Post by yabbadabbadont on 2007-06-21
You **cannot** use a fat32 partition for /home.....  fat32 does not support linux permissions and your login will never work correctly.

---

### Post by clitmaster on 2007-06-21
ahhh crap! haha! its pretty obvious now...that woulda been the prob the whole time! stupid me!

thanx 4 ya time anyways ninja!

---

### Post by hatchetjuggla on 2007-06-21
[COLOR="Silver"]probably not the same problem the whole time, on your PC you were mounting the fat32 drive IN /home, not AS /home. although, you were monting it as YOUR home wern't you?[/COLOR]


never mind.... re-read over everything... what the error looked like.... heh...

---

### Post by steveneddy on 2007-06-22
I may be old, but what did he say here:

[HTML]thanx heaps yabbadabbadont lol cool name btw...i hope i can b leet sauce 1 day helping noobs n ****
[/HTML]

someone interpret for me

---

### Post by yabbadabbadont on 2007-06-22
> **steveneddy said:**
> I may be old, but what did he say here:

[HTML]thanx heaps yabbadabbadont lol cool name btw...i hope i can b leet sauce 1 day helping noobs n ****
[/HTML]

someone interpret for me

You just didn't like that he want's to grow up to be like me one day instead of you...   :p :D  :lol:

---

### Post by steveneddy on 2007-06-22
> **yabbadabbadont said:**
> You just didn't like that he want's to grow up to be like me one day instead of you...   :p :D  :lol:

OK - but what did it mean?

I guess I'm too old.

(*mubbles....leet sauce? WTH? )

---

### Post by yabbadabbadont on 2007-06-22
> **steveneddy said:**
> OK - but what did it mean?

I guess I'm too old.

(*mubbles....leet sauce? WTH? )
Would had made more sense to you if he had used the phrase, "cool beans", instead?  ;)

---

### Post by clitmaster on 2007-06-25
leet sauce baby! wot dont u understand steven, want a diagram?? lolololol

as a follow up if any1 cares , ubuntuStudio's runnin sweet for me...now to learn/master these appz! ardour, audacity, etc... to get my audio engineering career off the ground! :D

---

