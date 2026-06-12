---
title: "No Synaptic, No Login Window, Update Manager No Workie!"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by atlien on 2007-02-23
I changed folder permissions to allow myself to copy **audio-convert** script to my bin folder.  I changed the permissions in terminal as I knew no other way to do it.  Now I have no **Synaptic Package Manager** function, no **Login Window** function and Update Manager says I have two security updates but will not install them after they download.

I tried a **sudo synaptic**.  

Terminal spits this back out:

**sudo: must be setuid root**

Anyone got any ideas?  Due to the fact that something is wrong with Synaptic I'm getting the feeling that this is all going to end up in a reinstall.  Please advise.:confused:

I'm also now noticing that my ipod will no longer mount.  So when I start gtkpod, the program doesn't recognize anything.  Up until these problems it always recognized and mounted without any assistance.  So no ipod mounting either.

---

### Post by spoot on 2007-02-23
You changed permissions of your /usr/bin/ folders and the like?

Perhaps you can just change them back with:

sudo chown -R root:root /usr/bin/
sudo chmod -R 755 /usr/bin/

(at least that is what my permissions are in all bin folders)

Or whatever folder you meant?

---

### Post by atlien on 2007-02-24
I'm going to give that a go.

What is the significance of 755?

---

### Post by atlien on 2007-02-24
It's just spitting back the 
**sudo: must setuid root** line.

Here is what I typed.
[B]sudo chown -R root:root /usr/bin
sudo chmod -R 755 /usr/bin[/B]

Any other ideas?  

I just went over to the bin folder to check and the permissions are still altered to where things can be copied and written by me.  

:-/

---

