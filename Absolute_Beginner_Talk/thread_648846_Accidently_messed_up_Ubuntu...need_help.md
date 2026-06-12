---
title: "Accidently messed up Ubuntu...need help"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2007-12-24
Yeah, uhh..

I raped the Ubuntu display, and I don't know how to get it back...I also got some other slight malfunctions which are "idiot problems" but I can't figure them out worth of damn.

[http://i82.photobucket.com/albums/j271/Syndacate/Computer%20Stuff/MUD.png](http://i82.photobucket.com/albums/j271/Syndacate/Computer%20Stuff/MUD.png)

A)  As you can see at the top, that is NOT how it's supposed to look :( - I was trying to remove something from one of the lists and I clicked "remove from panel" and it removed EVERYTHING from panel, I had to add it back but I could only get it back that way...there any way to revert to original...or at least create the dropdown lists again?  As they had everything, I just added whatever I could outta there..I liked the original setup, I want it back :(.

B)  I installed flash yesterday, from a .tar.gz file, which I extracted to a folder on my desktop.  i CANNOT delete it, what the hell?

It says I don't have permission to delete it...but when I check the permissions on the desktop and parent folders though Konsole (terminal), I get this:
*> drwx------ 5 syndacate syndacate 4096 2007-12-24 03:25 Desktop*
Uhh, k.
Now up one, my username, from the home folder...:
*> drwxr-xr-x 56 syndacate syndacate 4096 2007-12-24 04:05 syndacate*
OK
Now, on the Desktop:
*> drwxr-xr-x 2       501 users       4096 2007-11-20 18:24 install_flash_player_9_linux*

Yeah, what the shit? 

I finally JUST Removed it by going into the directory, then typed:
```

rm flashplayer-installer

```

It told me the file was write protected (even though I had access of "drwx" - then I typed:
```

sudo rm flash-player-installer

```

I couldn't use rmdir because the folder wasn't empty, and just "rm" failed.

Could anybody tell me what in the **** happened?  And why I couldn't delete it?

Also, I tried to "force" a remove by typing:
```

sudo rm -f install_flash_player_9_linux

```

To which it says -f isn't a valid remove option, so of course I typed:
```

rm --help

```

To which it replied a different help file (or an incomplete help file) than the one I just checked.

Should I have used **"-fd"** instead?

:(

I feel like a complete retard typing this, but this just got REALLY confusing, REALLY fast.  And my damn menu bar is GONE, I couldn't find konsole just now because I don't look at the icons usually :(

:'( - I want my stock *** panel back...

---

### Post by lgambett on 2007-12-24
sudo rm -r will do the trick. Please note, the -r stands for recursive. It will delete the directory specified and all the subdirectories inside, so BE CAREFUL ! The -f parameter is used to delete files specified as read only.

---

### Post by ~LoKe on 2007-12-24
Right click -> add to panel.  Then you should be able to add "gnome-main-menu" or something similar.

---

### Post by ~LoKe on 2007-12-24
Also note that it's very rare to need **sudo rm -rf** for anything.  Use it with CAUTION!!!!

```
sudo rm -R install_flash*
```
Would do the trick.

---

### Post by Syndacate on 2007-12-24
> **lgambett said:**
> sudo rm -r will do the trick. Please note, the -r stands for recursive. It will delete the directory specified and all the subdirectories inside, so BE CAREFUL ! The -f parameter is used to delete files specified as read only.

Yeah, I am careful.

It's just that -f wasn't going anywhere and it wouldn't delete it from the desktop.

Aight, so next time typing "sudo rm -r dir" will force remove a dir, and everything inside of it?

You have any idea why this happened?  Why would something get locked on write-protect on my desktop without my ability to access it..?

[quote=~LoKe]Right click -> add to panel. Then you should be able to add "gnome-main-menu" or something similar.[/quote]

Yeah, I can do that and add the ICON for the main menu, but there were like...words and such.  Like how it looked OEM, I like words - I don't like these mini-me icons :(

---

### Post by Syndacate on 2007-12-24
> **~LoKe said:**
> Also note that it's very rare to need **sudo rm -rf** for anything.  Use it with CAUTION!!!!

```
sudo rm -R install_flash*
```
Would do the trick.

Yeah, well apparently you need to use it to delete the folder extracted from the .tar.gz file if you download it/install it instead of using the apt-get command. :-\

---

### Post by meindian523 on 2007-12-24
Usually,deleting folders from which software has been installed from source is NOT recommended since then we can't use ```
make uninstall
``` to remove that particular app...........so just let be unless you are running dangerously low on hard-disk space......

Somebody correct me here if their experience suggests otherwise.....

---

### Post by ~LoKe on 2007-12-24
> **Syndacate said:**
> Yeah, well apparently you need to use it to delete the folder extracted from the .tar.gz file if you download it/install it instead of using the apt-get command. :-\

Nope.  You'd use sudo rm -R, not sudo rm -rf.

---

### Post by ~LoKe on 2007-12-24
> **Syndacate said:**
> Yeah, I can do that and add the ICON for the main menu, but there were like...words and such.  Like how it looked OEM, I like words - I don't like these mini-me icons :(

There's another entry for the menu.  There should be two.  One is the compact layout that you found, but there's a second that will have the three menus.

---

### Post by lgambett on 2007-12-24
rm -r and rm -R are absolutely the same, as you can see doing a
man rm
command

---

### Post by ~LoKe on 2007-12-24
> **lgambett said:**
> rm -r and rm -R are absolutely the same, as you can see doing a
man rm
command

I'm not comparing rm -R and rm -r, I'm comparing rm -r and rm -rf.

---

### Post by Paqman on 2007-12-24
> **Syndacate said:**
>  As you can see at the top, that is NOT how it's supposed to look :(

There's no way that panels are "supposed" to look. They're completely customisable. Right click and play around with adding and removing stuff. You can move panels around, change their behaviour and generally customise them to your heart's content. Personally I tend to ditch the bottom panel and just have a few system monitoring applets and the deskbar at the top.

---

### Post by lgambett on 2007-12-24
Ok. Without using the -f option every time you find a read only file you will be prompted to confirm deletion; without the -f deletion will proceed without warning.

---

### Post by ~LoKe on 2007-12-24
> **lgambett said:**
> Ok. Without using the -f option every time you find a read only file you will be prompted to confirm deletion; without the -f deletion will proceed without warning.

Correct.  The reason -rf is so dangerous is that if you were to mistype, or accidentally hit enter, and wind up entering...
```
sudo rm -rf / ## NOTE, DO NOT DO THIS
```
You'd end up destroying your installation.  However..
```
sudo rm -r / ## STILL, DON'T DO THIS
```
You'd get some advance warning that you're about to do something stupid.

---

### Post by Syndacate on 2007-12-24
> **meindian523 said:**
> Usually,deleting folders from which software has been installed from source is NOT recommended since then we can't use ```
make uninstall
``` to remove that particular app...........so just let be unless you are running dangerously low on hard-disk space......

Somebody correct me here if their experience suggests otherwise.....

It's a setup file from flash's website...?  It's not a system file.

I think you have them confused, it's not needed to run - never is.  It's just an installer to throw the system files in the right directories.  I don't know why it was write protected but it's gone now and flash works fine.  I don't want installer files on my desktop.

[quote=~LoKe]There's another entry for the menu. There should be two. One is the compact layout that you found, but there's a second that will have the three menus.[/quote]

Ahhaha, i didn't see the second one, one's called "main menu" - the other is called "main menu bar"

-- I love you :-P

So if I used the recursive option it still would have overridden the write protect on the file inside the folder?  Or would I have had to use sudo rm -rf ?

I thought "force" was to override all the write protection crap, no?  I'm perplexed as to why sudo rm -f didn't work...

[quote=lgambett]rm -r and rm -R are absolutely the same, as you can see doing a
man rm
command[/quote]

He wasn't saying they were different, one only had the -r option, the other had -r[b]f[b]

---

### Post by Syndacate on 2007-12-24
> **Paqman said:**
> There's no way that panels are "supposed" to look. They're completely customisable. Right click and play around with adding and removing stuff. You can move panels around, change their behaviour and generally customise them to your heart's content. Personally I tend to ditch the bottom panel and just have a few system monitoring applets and the deskbar at the top.

Ah,s orry , forgot about the whole "customizable" thing.

Yeah, my wording dictionary:
"supposed to" = "stock" = "OEM"

I get what you're saying, but that's what I meant, sorry for the confusion.

Wow, it appears 50,000 people replied in the time it took me to make one post...

[quote=~LoKe]Correct. The reason -rf is so dangerous is that if you were to mistype, or accidentally hit enter, and wind up entering...[/quote]

Oh, ****, yeah, I didn't even think about the whole mis-typing and putting a space after the first / having "sudo rm -fr /" - the famous "linux nuke" command - heard it mentioned a few times in my Java class.

Gah, yeah, good point :-X

EDIT:
Yeah, I wanna stay away from that command now, lol

What would have you done in the same position?  Folder on Desktop with a write protected file inside, to which "sudo chmod +rwx" to the file said I was unable to do...?

---

### Post by meindian523 on 2007-12-25
I didn't say it was required to **RUN**,I said it was required to **UNINSTALL** in case you ever wanted to.......

---

### Post by Syndacate on 2007-12-26
> **meindian523 said:**
> I didn't say it was required to **RUN**,I said it was required to **UNINSTALL** in case you ever wanted to.......

Oh, gotcha.

Yeah, but apt-get should still be able to install it without that, though i could be wrong.

---

### Post by HermanAB on 2007-12-26
Tip: If you accidentally mess up your system, just re-install.  That is usually easier and faster than to try and figure out what went wrong.  Eventually, you'll get to know the system better and you will be able to fix most things, but for starters, re-installing is a good strategy.

---

### Post by Syndacate on 2007-12-26
> **HermanAB said:**
> Tip: If you accidentally mess up your system, just re-install.  That is usually easier and faster than to try and figure out what went wrong.  Eventually, you'll get to know the system better and you will be able to fix most things, but for starters, re-installing is a good strategy.

That's what I was thinking, thanks for the clarification.

---

### Post by Martje_001 on 2007-12-26
Don't reinstall! Just remove all 'dot'-directory's and you're back to default.

Command:
```
rm -rf .*
```

Take care!

---

### Post by Syndacate on 2007-12-26
> **Martje_001 said:**
> Don't reinstall! Just remove all 'dot'-directory's and you're back to default.

Command:
```
rm -rf .*
```

Take care!

For some reason that command appears semi-suicidal...

Can somebody else confirm whether if I typed this the apocalypse would happen?

What do the 'dot" directories do?

---

### Post by LaRoza on 2007-12-26
> **Syndacate said:**
> For some reason that command appears semi-suicidal...

Can somebody else confirm whether if I typed this the apocalypse would happen?

What do the 'dot" directories do?

The directories that begin with a dot are hidden and are used to store settings. Deleting them will make the apps create default configuration directories.

(I didn't read this thread, just answering that post)

---

### Post by meindian523 on 2007-12-26
That's correct...ie the one about rm -rf .* deleting your personal settings and forcing the apps to recreate default settings..........

---

### Post by LaRoza on 2007-12-26
> **meindian523 said:**
> That's correct...ie the one about rm -rf .* deleting your personal settings and forcing the apps to recreate default settings..........

Someone has been reading people's sigs about the danger of such commands it seems, I guess it worked.

---

### Post by meindian523 on 2007-12-26
yeah,and that's why I added my "all-clear" to give the OP more confidence.......had that Announcement link in my sig too till a few days ago........

---

### Post by Syndacate on 2007-12-26
> **LaRoza said:**
> The directories that begin with a dot are hidden and are used to store settings. Deleting them will make the apps create default configuration directories.

(I didn't read this thread, just answering that post)

**Everything** will be default?  Like I'll lose my browser homepage/settings and such?

---

### Post by LaRoza on 2007-12-26
> **Syndacate said:**
> **Everything** will be default?  Like I'll lose my browser homepage/settings and such?

Yes, but you can save that, by copying the directory and then putting it back. 

.firefox, .opera and whatever browser you use, copy their settings to somewhere safe (or rename them, get rid of the dot then add it back after)

---

### Post by Syndacate on 2007-12-26
Okay, gotcha.

I'll keep that in mind for next time, for this time though, somebody told me how to get 'em back on like the 1st or 2nd page.

Thanks a lot though, I'll probably have to use that in the future with my linux skill level :P.

---

### Post by buccaneere on 2007-12-26
> **Syndacate said:**
> Yeah, uhh..


[http://i82.photobucket.com/albums/j271/Syndacate/Computer%20Stuff/MUD.png](http://i82.photobucket.com/albums/j271/Syndacate/Computer%20Stuff/MUD.png)
.

Pretty nifty display there, buddy!

How do I get mine like that?

---

### Post by Martje_001 on 2007-12-26
> **Syndacate said:**
> For some reason that command appears semi-suicidal...

Can somebody else confirm whether if I typed this the apocalypse would happen?

What do the 'dot" directories do?
Yes, sorry. I should have explained it. If you only remove .gconf2 and .gnome2 you should be fine too (but I'm not sure of that).

---

### Post by Syndacate on 2007-12-26
> **buccaneere said:**
> Pretty nifty display there, buddy!

How do I get mine like that?

Kubuntu + Ubuntu (GDE/Gnome) Desktop Environment.

EDIT:
If you meant the gaycons at the top - just right click the "words" - and hit "remove from panel" - then right click the panel, and hit "add" - and then you can add the small icons.

---

