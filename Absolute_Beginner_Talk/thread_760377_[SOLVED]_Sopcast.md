---
title: "[SOLVED] Sopcast"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Smudger on 2008-04-20
Right here we go.

I have downloaded sp.auth.tgz and libstdcpp5.tgz.

What do I do now, please take into account I am completely new to Ubuntu and have no knowledge of how to do anything.

Many Thanks

Smudger

---

### Post by rburkartjo on 2008-04-20
try this link
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
senior cheesemaker

---

### Post by Hieronymus on 2008-04-20
Check this site: [http://www.ubuntu-unleashed.com/2008/02/howto-watch-p2p-tv-with-sopcast-with.html](http://www.ubuntu-unleashed.com/2008/02/howto-watch-p2p-tv-with-sopcast-with.html)


Regards, 

Jeroen

---

### Post by Smudger on 2008-04-20
Im just baffled now.

Not got a clue what to do :(

---

### Post by Hieronymus on 2008-04-20
Ok, I'll start on writing an step-by-step guide. In the mean time, do you have an msn account? That works a bit faster, if you have just add me to you messenger (my adress is in my profile).

Jeroen

---

### Post by Smudger on 2008-04-20
> **Hieronymus said:**
> Ok, I'll start on writing an step-by-step guide. In the mean time, do you have an msn account? That works a bit faster, if you have just add me to you messenger (my adress is in my profile).

Jeroen

OK cheers, have added you to my msn account.

---

### Post by atomkarinca on 2008-04-20
You can use the .deb file I have attached. Just double-click and you're good to go.

---

### Post by sandysandy on 2008-04-20
how do u find sopcast

regards

---

### Post by Smudger on 2008-04-20
> **atomkarinca said:**
> You can use the .deb file I have attached. Just double-click and you're good to go.

Tried that got an error saying **[COLOR="Red"]Dependency is not satisfiable: sopcast[/COLOR]**

Any ideas how to fix this problem?

---

### Post by NOLU on 2008-04-20
If anything I try to watch using Sopcast freezes after a few seconds, like it plays briefly then lock up, is that more down to my connection or speed?

The whole idea of me getting rid of Sky Sports was to watch games on the computer but since I've had no joy with Sopcast.

---

### Post by Hieronymus on 2008-04-20
@smudger: to make sure everyone can see the answer to your question I also post it here.

With thanks to [**tombott**]("http://ubuntuforums.org/showthread.php?p=3972826#post3972826")

```

# Get the GSopcast GUI deb file
wget [http://freetowatchtv.co.uk/images/ub...2.8-1_i386.deb]("http://freetowatchtv.co.uk/images/ubuntu/gtk-sopcast_0.2.8-1_i386.deb")

``````

# Install the deb
sudo dpkg -i gtk-sopcast_0.2.8-1_i386.deb

``````

# get the newest version of sopcast
wget [http://freetowatchtv.co.uk/images/ubuntu/sp-auth.tgz](http://freetowatchtv.co.uk/images/ubuntu/sp-auth.tgz)

``````

# extract it
tar xzf sp-auth.tgz

``````

# move the sopcast executable to the directory where the GUI requires it to be and renaming it (the newest version from sopcast is named sp-sc-auth and not sp-sc)
sudo cp sp-auth/sp-sc-auth /usr/bin/sp-sc

``````

# root should own the sp-sc executable - probably not required
sudo chown root:root /usr/bin/sp-sc

```

The link to Sopcast should now be in you Sound & Video menu

Regards, 

Jeroen

---

### Post by Smudger on 2008-04-20
Just like to say a big thanks to everyone who has helped me resolve this problem.

Most of all Hieronymus, who was a massive help.

=D>=D>

---

### Post by johnmc on 2008-04-22
Very simple and clear guide here from Hieronymus - thank you very much!
I got it working but when trying to open links from the web (I implemented the necessary sop entry in the about:config) only gsopcast opens and shows the usual channellist... that's it. nothing more happens. What am I doing wrong?
Any help would be appreciated, thanks!

---

### Post by atomkarinca on 2008-04-23
> **johnmc said:**
> ...when trying to open links from the web (I implemented the necessary sop entry in the about:config) only gsopcast opens and shows the usual channellist... that's it. nothing more happens. What am I doing wrong?

I guess this was supported after version 0.4. You can find the .deb file on my previous post, on the first page.

---

### Post by johnmc on 2008-04-23
nice, that seems to have fixed the problem! thanks!

---

### Post by atomkarinca on 2008-04-23
> **johnmc said:**
> nice, that seems to have fixed the problem! thanks!

Not a problem.

---

