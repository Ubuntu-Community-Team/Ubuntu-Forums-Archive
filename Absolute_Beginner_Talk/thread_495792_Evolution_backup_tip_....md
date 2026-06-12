---
title: "Evolution backup tip ..."
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-07-08
Hi,

It's Sunday night and time for the weekly backup. anyway, found this really handy tool to backup and restore  Evolution's mail folders, contacts ect. 

It's not a detailed export tool like outlook, but it's darn quick and handy to backup the entire .evolution folder and then to restore it again. New people who don't like mucking around with the terminal to much (I think) will find this very handy.

> sudo apt-get install evolution-plugins-experimental


After it's done, open up evolution, click on File, click on backup settings. There are no settings, LOL. just select a file name and It'll create a tar file with all of your evolution data in it - Evolution will close without warning, and after the backup is done, reopen. The restore is just as simple.

Cheers,

Rudolf

---

### Post by zero244 on 2007-07-08
Hello Sounds like a nice idea I tried the command and it said it couldnt find the package.
Thanks for the tip.

---

### Post by RudolfMDLT on 2007-07-08
Weird....

I just tested that again and it works. 

Press Alt+F2 and enter **gksu gedit /etc/apt/sources.list**

Check that all the repo's are UN-commented. ie, if there is a # infront of a URL, un comment it. then in the terminal do a "sudo apt-get update" and then try the command  in the first post.

Cheers,

Rudolf

---

### Post by zero244 on 2007-07-08
I just did what you said and it stil didnt find it.
I am using Edgy could be its not in the repos.
If I use Synaptic it finds the backup-restore pluggin the the pluggin package but it didnt install the experimental sfuff for some reason.

---

### Post by freesitebuilder on 2007-07-08
hmm .. works, but it will only create file in ~home, even if I change the folder in the "save" dialogue. But I should be moving it to removable media anyway, so I suppose it doesn't matter. :)

---

### Post by dwiedenfeld on 2007-08-14
So, where are the email, contacts, etc. files located? You mention a .evolution folder, but I can't find it.

---

### Post by RudolfMDLT on 2007-08-15
Hi there,

In Ubuntu, folders with a period preceding the name of the folder are hidden folders. 

In Nautilus(the default file browser) go to your home folder and press CTRL+H - and they should appear.

Cheers,

Rudolf

---

### Post by dwiedenfeld on 2007-08-19
Thanks--perfect. I didn't know that (that .name files are hidden)--that's why it's "Absolute Beginner Talk".  I appreciate it.
David

---

### Post by AbredPeytr on 2007-08-19
Thanks for the tip!  I installed it from Synaptics and it works like a charm.

---

### Post by ityro on 2007-08-19
Thanks. I have a manual backup for Evolution but this is much better. Thanks again.

---

