---
title: "Borked my xorg?"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by cdi3d on 2006-05-20
(can I even say that in a public forum? *gasp* ;-) )

Seriously though. 

Been playing around with how my desktop looks and I enabled translucency in a setting. Well it started crashing the composite manager. So being a freshly planted forumite I went looking for tips. Found one explaining the exact error I was getting and how to correct it. 
Followed it and now x wont start. 
It gives me a few errors such as 

font render "name of font" already registered at priority 0
and
x10 fatal IO error 104 

Now I made (not ONE but) two back ups of the original xorg_conf before I edited it (cmon people gimme a cookie for this..newbie do good!) 
But I cant copy the backup data to the borked conf file. 
err: cp: cannot stat '/etc/X11/xorg.conf_back': No such file or directory

*chuckle* 

Maybe its my command (still memorizing) its:
sudo cp (backup path and file) > (shiney fresh path and file)

And I need the ">" in there correct?

---

### Post by glotz on 2006-05-20
:)

No, there must be no >. I've never tried that and dunno what it'd do. Intuitively it probably should work, but...

just sudo cp [source] [target]

---

### Post by cdi3d on 2006-05-20
[QUOTE=glotz]:)

No, there must be no >. I've never tried that and dunno what it'd do. Intuitively it probably should work, but...

just sudo cp [source] [target][/QUOTE]

Thanks Lotz,

I feel like this is the beginning of my trial by fire experience with ubuntu. *chuckle*

Nope when I do that, I get a "no such file or directory" for my backup file even though ls shows them right there.

---

### Post by catlett on 2006-05-20
I didn't read through your errors. I just saw the title and thought I would post the command to reconfigure your xserver. This command takes you to the steps from the install.
```
sudo dpkg-reconfigure xerver-xorg
```
Don't know if it helps your situation but it starts your configuration from scratch and then you reenter your setting all over again.

---

### Post by cdi3d on 2006-05-20
```
sudo dpkg-reconfigure xerver-xorg
```
Don't know if it helps your situation but it starts your configuration from scratch and then you reenter your setting all over again.[/QUOTE]


Hi cat.

Yah Im familiar with that command but I was trying to avoid it. Was trying to edit my way to a fix. Shoot if I could just get the conf file to display I can remove the lines I added! But it wont display

---

### Post by catlett on 2006-05-20
Launch nautilus as root and browse to the file. If it exists you'll be able to open and edit in nautilus as root```
 gksudo nautilus
```

---

### Post by glotz on 2006-05-20
[QUOTE=cdi3d]T
Nope when I do that, I get a "no such file or directory" for my backup file even though ls shows them right there.[/QUOTE]

You're aware that Linuxes are case sensitive? a != A

(=got any CAPS in your backup filename?)

---

### Post by cdi3d on 2006-05-20
[QUOTE=glotz]You're aware that Linuxes are case sensitive? a != A

(=got any CAPS in your backup filename?)[/QUOTE]

Yuppers, case sensitive. Got it. No caps in the back up. 

Thanks Cat and Lotz. 

Got it working again by ...der...following another tip here in the forums. 

Question: The newest tip i followed advised shutting down KDM...since I was already in a command line environ I had thought KDM was already down...but it wasnt...could that be why I was having so much trouble?

Anywho got the conf file opened in nano, removed the added extention lines and BAM Im back in ubuntu.

Think Ill put up with the crashes till dapper gets released.

---

