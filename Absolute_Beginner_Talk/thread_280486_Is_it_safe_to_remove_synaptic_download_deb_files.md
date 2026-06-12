---
title: "Is it safe to remove synaptic download deb files?"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Ba|der on 2006-10-19
After new updates and after I have installed a new program via the repository the downloaded .deb files seems to be hanging around in /var/cache/apt/archieves/. This takes up HDD-space that I else could use to other things. Is it safe to just remove them or will it cause trouble with future updates and the marking of installed programs in Synaptic?

---

### Post by jordanmthomas on 2006-10-19
It is safe to delete them:
```
sudo apt-get clean
```

Beware, though, as in the case of a faulty upgrade (like the xserver back in September) you won't have the old ones any more, which will complicate fixing things a little bit.

I clean mine out regularly though.

---

### Post by ThrobbingBrain66 on 2006-10-19
yes, you can delete those safely.

```
sudo apt-get clean
```

will do the job nicely for you.

EDIT: ahh!  i got beat!

---

### Post by glug101 on 2006-10-19
I'm not at my Ubuntu machine right now so I cannot tell you where to find this, but I'm sure there is an option in Synaptic for deleting the downloaded deb files automatically.  Or, you could run an install of a program from 'dselect' on the command line and that will prompt you to automatically delete downloaded deb files.

Edit: Wow, was I outpaced and out classed on that one.  That's what I get for answering posts between phone calls....

---

### Post by Grey on 2006-10-19
Yeah, and just so you know, you can delete them with "sudo apt-get clean".  ;)

---

### Post by Ba|der on 2006-10-20
Thanks for all your replies. I had originally intended to just remove them in the file managar or with rm on the commandline. I found the option in Synaptic and removed the packages and selected to not keep deb.files for future updates. I've never seen 'dselect' before, it looks too me as a inhertiage from debian and that Synaptic have replaced it?

---

