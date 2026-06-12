---
title: "DOCX in OpenOffice"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by P3RH4PS on 2007-10-08
I've tried [this]("http://ubuntuforums.org/showthread.php?t=386385") way and [this]("http://www.sigmundvoid.com/?p=81") way and mine just says "File blah blah blah is not found"  So I know this is a real novice question, but what am I doing wrong?  The odf-converter-1.0.0-5.i586.rpm file is on my desktop.  I've tried using:

alien -ct odf-converter-1.0.0-5.i586.rpm
alien -ct /home/preston/Desktop/odf-converter-1.0.0-5.i586.rpm
sudo alien -ct odf-converter-1.0.0-5.i586.rpm
sudo alien -ct /home/preston/Desktop/odf-converter-1.0.0-5.i586.rpm

And a lot of other really stupid renditions of the above code.  WTF is wrong with my skillz?

---

### Post by forestpixie on 2007-10-08
I did it with

```
cd Desktop
```

```
sudo alien odf-converter-1.0.0-5.i586.rpm
```

then you should get a deb to dbl clk

---

### Post by P3RH4PS on 2007-10-08
Well, I got the rpm to deb, but now my copying is giving me a similar problem:

```
preston@presdesk:~$ sudo cp usr/lib/ooo-2.0/program/OdfConverter /usr/lib/openoffice/program/
cp: cannot stat `usr/lib/ooo-2.0/program/OdfConverter': No such file or directory
preston@presdesk:~$ 
```

I know that's probably something simple but can someone tell me why my comp keeps telling me that files don't exist when I have found them manually?  I am really new to this whole thing and my troubleshooting doesn't seem to get me very far.

---

### Post by Tom Mann on 2007-10-08
Have a look at the 3rd post here. And good luck! :)

[http://ubuntuforums.org/showthread.php?t=386385](http://ubuntuforums.org/showthread.php?t=386385)


They talk about fakeroot on this post, which can be got by ```
sudo aptitude install fakeroot
```

---

### Post by conor on 2007-10-23
If this will help anyone I made myself a script...
do anything with it..  I'd rather it get used

---

