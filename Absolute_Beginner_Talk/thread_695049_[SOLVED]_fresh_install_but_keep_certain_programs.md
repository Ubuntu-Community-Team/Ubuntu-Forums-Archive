---
title: "[SOLVED] fresh install but keep certain programs?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by linux5uper on 2008-02-12
Hi all,

After a few years of tinkering with various distributions, I have finally moved permanently to gnu/linux and managed to get everything working perfectly. 

With the approach of the new LTS release, there's a question that I couldn't find the answer to. Assuming I have a separate /home partition, and I have one particular proprietary program (matlab) that is installed in my home partition, how can I restore the system-wide links and associations for this program after a fresh install, without reinstalling the program from scratch (so as not to bother the super-busy IT guy at my department)?

If you can point me to a general article on how linux application installations work and where files are put, that would be awesome too! (i.e. windows puts stuff in program files + adds keys to registry + adds shared program files etc., how is this for linux?)

Thanks a lot for your help!

---

### Post by jan quark on 2008-02-12
well linux stores installed application not together in a Folder A

but by the type of the files

so all types of files 1 go into this folder
all types of files 2 go into another folder

the application is scattered in many places

---

### Post by linux5uper on 2008-02-12
Thanks! That doesn't sound too good then.

Is there a way of finding out where the files for a particular app went? I don't mind CLI & config files at all.

---

### Post by PeterJS on 2008-02-12
If it was installed as a deb package, you can search for it in synptic, and one of the options in there if you right click and select properties is to list all of the installed files.

As for how things are "scattered" the FHS defines what goes where and why, and it wiki article on it covers it pretty well:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by linux5uper on 2008-02-12
Thanks, this is exactly what I imagined I was looking for. The keywords I used were a bit different though, and didn't give anything useful on Google.

This particular app had its own ./make install script, but I suspect it didn't scatter files too much, just the binary links to the shell and associated mime filetypes.

Thanks again UbuntuBeginnersTeam, I am thoroughly impressed by the swiftness of your responses :)

---

### Post by Whiffle on 2008-02-12
Just a side note, next time you compile something from source, get checkinstall, and instead of make install, do checkinstall.  It will make a deb package for you, which you can backup and save :)  


Also I read your post again, if its in your home directory and you installed it in your home directory as you and not a root/super user, it should all be in your home directory, including links and associations, since you don't have permission to write anywhere else.

---

### Post by linux5uper on 2008-02-12
> **Whiffle said:**
> Just a side note, next time you compile something from source, get checkinstall, and instead of make install, do checkinstall.  It will make a deb package for you, which you can backup and save :)  


Also I read your post again, if its in your home directory and you installed it in your home directory as you and not a root/super user, it should all be in your home directory, including links and associations, since you don't have permission to write anywhere else.

That's a cool tip, I hadn't heard about checkinstall before!

I had to provide my su pass during installation, but I searched my filesystem for 'matlab' now and I only found 3 files outside of the /home partition in the following folders:

/usr/local/bin (type:link to shell script)
/usr/share/apps/katepart/syntax (type:xml document)
/usr/share/mime/text (type: xml document)

Hopefully these are the only ones, otherwise I'll learn next time :)

---

### Post by PeterJS on 2008-02-12
> **linux5uper said:**
> That's a cool tip, I hadn't heard about checkinstall before!

I had to provide my su pass during installation, but I searched my filesystem for 'matlab' now and I only found 3 files outside of the /home partition in the following folders:

/usr/local/bin (type:link to shell script)

That's how matlab links itself to the path, so that you can just run (I'm assuming this is what it's called, but you get the idea) matlab in a terminal and have the system find it. It's nice, it's not strictly required, and not that hard to set up by hand. (just recreate the link).
> 
/usr/share/apps/katepart/syntax (type:xml document)

That's the xml file that defines how kate should implement syntax highlighting for matlab programs. It's a nice feature to have if you use kate, but not so useful if you use a different text editor. If you use kate you might want to keep a copy of that handy.
> 
/usr/share/mime/text (type: xml document)

I'm not entirely sure how the mime associations work, but I'd bet that that's related to setting up the extension and/or magic handlers for matlab files.
> 
Hopefully these are the only ones, otherwise I'll learn next time :)
It wouldn't be learning if you knew it all from the start now would it :)

EDIT:
Oh yeah, and checkinstall is in the running for one of the best things ever.

---

### Post by zozobra on 2008-02-12
Also, if you'd like get a general idea of where all that relative information is held, you could run 

```
sudo updatedb
```
then
```
locate *applicationname*
```

---

### Post by linux5uper on 2008-02-12
Thanks guys, you're awesome.

---

