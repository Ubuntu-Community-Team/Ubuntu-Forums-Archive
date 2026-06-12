---
title: "No Internet"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by jrchairez on 2007-01-30
The only way I get online is through work, I can't seem to find a way to install wine or any other files without the internet.  I tried to download it to a disk and then install it at home but it gets even more confusing.  I want to break away from Windows, but it seems like this is 5 times harder to deal with.  It seems like all of the programs worth using are only available online through synaptic.  I am starting to resent Ubuntu for this.  Can some one help explain this for me?

---

### Post by rabid9797 on 2007-01-30
is there a problem with ubuntu not being able to connect to the internet or do you just not have internet at home?

---

### Post by batholith on 2007-01-30
if you are supposed to have internet at home make sure you give some details on whether you have dial-up, dsl, or wireless capabilites (or lack thereof...)

---

### Post by Steggy on 2007-01-31
If I'm reading your post right and you mean that you don't have Internet access from home, then you'll need to download the .deb files for the various programs you want to install.

You can find the .deb files at packages.ubuntu.com. When you search for and find a package you want, make sure to pay attention to what the site lists as dependencies--these will have a red circle next to them. You'll need to grab all of those packages as well (or at least the ones not already installed on your system.) You can also look at the reccommended and suggested packages as well and decide if you want to install those, too.

Once you get the files to your home computer, copy them into your home directory. Then you can install them with this command (in the terminal):

 ```
sudo dpkg -i ~/package-name-here.deb
```

Obviously, insert the actual package name into the command.

After that, it will ask for your password. Once you enter it, dpkg will install the package for you.

One additional note, make sure you install all dependencies of a package before you try to install the package itself--otherwise, dpkg will return an error about the dependencies being unmet.

Hope this helps. :)

---

### Post by jrchairez on 2007-01-31
Sorry, prehaps I should have made my situation more clear.  I don't have the internet at home, I was given an install CD from a store.  "Free" was all I needed to hear.  Thank you Steggy I will try your advise.  I can get the internet from a neighbor/friend via my Dlink dwl-g120,  but that is a whole different ballpark.  As I gain experience I will give it a try.  But thanks Steggy for now.  :D

---

