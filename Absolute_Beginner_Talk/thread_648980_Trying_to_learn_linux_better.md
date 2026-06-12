---
title: "Trying to learn linux better"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Mular on 2007-12-24
So I installed firefox beta 3 via this guide [http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html]("http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html")

Now the question is if I wanted to go back to firefox 2.0 how would I do that? what is the point of the sudo dkpg-divert command? Also in that guide it talks about /usr/lib/mozilla-firefox - I never had that directory? 

Basically I don't actually want to go back, but I want to learn how I would. I don't quite get how installing works.. I think all I did with this guide was move files around and replace the old firefox with this new one?

---

### Post by Perpetual on 2007-12-24
Actually, you should still have Firefox 2 installed as Firefox 3 installs as a seperate app.

---

### Post by Mular on 2007-12-24
I don't know I think it overwrote it.. because I can't find anything..

When you install a program does it all get saved under /usr/lib?

And whats the point of usr/bin? Is there where all your "shortcuts" are saved? Like when I click the icon for firefox is it looking at usr/bin/ firefox then its being "redirected" to /usr/lib/firefox ?

I guess what I am asking is just in general how are programs installed in linux as opposed to windows?

---

### Post by The Cog on 2007-12-24
Your old firefox is probably still there. Try this command:
**/usr/lib/firefox/firefox**

The dpkg-divert probably changes the file in /usr/bin to be a symbolic link pointing to whichever real firefox file you tell it to, but I don't know the details.

---

### Post by Mular on 2007-12-24
> **The Cog said:**
> Your old firefox is probably still there. Try this command:
**/usr/lib/firefox/firefox**

The dpkg-divert probably changes the file in /usr/bin to be a symbolic link pointing to whichever real firefox file you tell it to, but I don't know the details.

Yeah you know what your right.. I just figured this out before I saw your post..

I guess basically if my understanding is right firefox 3.0 is saved to my /opt folder.. whereas firefox 2.0 is saved to /usr/lib..

what the dpkg-divert did what you said, changed all my links in /usr/bin from firefox.ubuntu and mozilla.firefox.ubuntu to firefox and just mozilla-firefox..

Then using sudo ln -s it then overwrote the /usr/bin links to go to /opt/firefox.. 

I think this is right.. Now my question is why use the dkpg-divert? I mean couldn't you just delete the links and make new ones? Or even couldn't you just use mv to rename the files? I am sure theres a reason I just don't understand it lol..

Thanks for the help!

---

### Post by nick_h on 2007-12-24
When you install your new version firefox you change the symbolic link /usr/bin/firefox to point to your new version instead of the old one.  The problem with this is that /usr/bin/firefox is part of the firefox package in the repositories.  If the firefox package has updates then it may well overwrite /usr/bin/firefox and change it back to a link that you don't want.

dpkg-divert is part of the package management sytem that overcomes this problem.  It allows you to divert any updates to a file to another location.  In this case if the firefox package wanted to update the /usr/bin/firefox file the update would actually be diverted to the file /usr/bin/firefox.ubuntu

You can see all the current diverts with:
```
sudo dpkg-divert --list
```

If you wanted to remove the divert to return to your original you would use:
```
sudo dpkg-divert --rename --remove /usr/bin/firefox
```

---

