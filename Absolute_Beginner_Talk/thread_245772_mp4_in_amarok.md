---
title: "mp4 in amarok"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Kleist on 2006-08-28
Could anyone tell me how I can play mp4 files in amarok?

I think I have all plugins installed and actually I can play a single mp4 file in amarok with "open media" etc...
But when I scan my folders with mp4 files, amarok doesn't add them to my play list. Of course I can add individual files, but it's not much fun when I have about 500 mp4 files. 

I've been reading other posts, but I can't find the solution to my problem.

I have amarok 1.3.9
and ubuntu 6.06

Thanks.

---

### Post by davebgimp on 2006-08-28
You might try upgrading to a newer version of amaroK.

If you do want to try that (works for me), add this line to your sources.list:

**deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main**

You may need to add the GPG key for this repository, so open a terminal and type:

**gpg --keyserver subkeys.pgp.net --recv DD4D5088**

and then:
**gpg --export --armor DD4D5088 | sudo apt-key add -**

After the key's been added, type:
**sudo apt-get update**
and then:
**sudo apt-get upgrade**

That will get you the latest amaroK for Kubuntu. You might want to back up your amaroK user files first (not your music, just your stats, config and cover image cache-your music files will be fine). I think that when I upgraded, my library was rebuilt as new, but since that doesn't affect my music, I didn't care.

---

### Post by Kleist on 2006-08-28
Thanks for answering my question.

I tried what you said, but nothing happens. I got this after  


**sudo apt-get upgrade**...

[B]Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/B]

I added the line 
[B]
deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main[/B]

to **/etc/apt/sources.list**

Is this the correct file?

---

### Post by Kleist on 2006-08-28
I could install amarok following this:

[http://www.imbrandon.com/2006/08/23/get-it-hot-amarok-142-released/](http://www.imbrandon.com/2006/08/23/get-it-hot-amarok-142-released/)

Thanks

---

