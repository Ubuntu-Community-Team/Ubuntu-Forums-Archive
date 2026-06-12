---
title: "sudo gedit not working? I'm lost..."
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by freshofftheufo on 2006-11-11
I'm installing azureus for the nth time due to battles with Java, and I'm trying not to use the package manager because it doesn't seem to install the version that I want it to. I think this step is for creating the azureus entry in the Applications menu:

```
sudo gedit /usr/share/applications/azureus.desktop
```

It doesn't work; just nothing happens. If I don't "sudo", it opens gedit, but of course then the permissions don't work so I can't save it.

What's wrong here? Why won't gedit open when I put sudo in? I've checked and there are no other instances of gedit running.

---

### Post by taurus on 2006-11-11
> **freshofftheufo said:**
> I'm installing azureus for the nth time due to battles with Java, and I'm trying not to use the package manager because it doesn't seem to install the version that I want it to. I think this step is for creating the azureus entry in the Applications menu:

```
sudo gedit /usr/share/applications/azureus.desktop
```

It doesn't work; just nothing happens. If I don't "sudo", it opens gedit, but of course then the permissions don't work so I can't save it.

What's wrong here? Why won't gedit open when I put sudo in? I've checked and there are no other instances of gedit running.
Please use

```
gksudo gedit /usr/share/applications/azureus.desktop
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by DaveBorealis on 2006-11-11
Hello,

Maybe gedit isn't in the path available when using sudo.

You could try getting the complete path for gedit:
```
 which gedit
```
(On my system it's '/usr/bin/gedit'.)

And then run the command like so:
```
sudo /usr/bin/gedit /usr/share/applications/azureus.desktop
```

Or:

```
gksudo /usr/bin/gedit /usr/share/applications/azureus.desktop
```

HTH,
Dave

---

### Post by freshofftheufo on 2006-11-11
I'm pretty sure gedit is in the path; it has worked for everything until now, it just stopped working when I tried this time.

I tried gksudo before, and it gave some kind of error... like "unable to connect" to something or other, I can't remember. I just tried it again and it said GNOME_SUDO_PASS and nothing happens unless I cancel the process.

I tried sudo again, and now it actually asks for the password first, but it still doesn't do anything...

[EDIT]

I get the same error as before now when I try gksudo:
```
(gedit:18697): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

No idea...

---

### Post by DaveBorealis on 2006-11-11
What happens if you open a terminal window and open it with nano?

```
sudo nano /usr/share/applications/azureus.desktop
```

[edit]BTW, '/usr/share/applications/azureus.desktop' is a file and not a directory, right?

---

### Post by bulldog on 2006-11-11
Is the document you want to open available?
Maybe you ask something that can't be done.

Check if there's a file called azureus.desktop.

---

### Post by freshofftheufo on 2006-11-11
No there is no file, it's supposed to create a new file. If I try to save the new file without sudo then it won't let me create it, so I guess that's why it was written this way.

I'm just following the directions from the ubuntu guide.

---

### Post by DaveBorealis on 2006-11-11
Create the file first,
```
sudo touch /usr/share/applications/azureus.desktop
```
and then see if you can gksudo edit to open it.

You might also have to
```
sudo chmod 644 /usr/share/applications/azureus.desktop
```

---

### Post by freshofftheufo on 2006-11-11
"touch" worked but it still wouldn't open gedit.

I tried it with "nano" now and it worked, so thanks for that. I still don't know what's wrong with gedit, it was working fine yesterday.

It seems that it wont work with "sudo", though it works fine for everything else...

---

### Post by DaveBorealis on 2006-11-11
And if you try gksudo gedit /usr/home/<user>/<sometextfile.txt> that also doesn't work?

---

### Post by digby on 2006-11-11
Have you tried with another text editor such as nano or vi?

---

### Post by freshofftheufo on 2006-11-11
Yes, nano worked no problem. It's just strange that gedit would give me that kind of trouble with sudo, because it has been working fine until now and I haven't changed it in any way.

gksudo doesn't work either, depending on if I try it fresh or "in a row" the error message was different; I wrote both of them above.

---

### Post by rolando on 2006-12-26
I too have suddenly had this problem, after installing a software update no doubt

Still XGL and nm-applet make up for things that dont work sometimes...

back to vi I guess.

C-ya

---

### Post by rolando on 2006-12-26
Oh yeah, I forgot

Try sudo nautilus, it wont work either

Its a Gnome issue for sure.

Maybe ill delete my .gnome directories

---

### Post by taurus on 2006-12-26
```
gksudo nautilus
```

---

