---
title: "Error Message in Synaptic"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by CybaCowboy on 2006-05-10
When I load the Synaptic Package Manager, I am told:
*W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)*

I never used to get this error message, so obviously *something* is wrong, but how do I fix it?

---

### Post by gibson on 2006-05-10
appears like you have modified your sources.list file, can you post this.

also, try

```
sudo apt-get update
```

from command line

hth

---

### Post by lodravah on 2006-05-10
[http://ubuntuforums.org/showthread.php?t=173363](http://ubuntuforums.org/showthread.php?t=173363)

I got the same error message. It seems that the link is dead and is pointing to the "Listen"-program for Gnome. I went into source.list and put the "#" in front of the link and the message went away. But check out the link i pasted, 'cause it is to my own post with the same problem. I got help, and now I hope I'm helping you..

lodravah

---

### Post by CybaCowboy on 2006-05-10
It appears to install a whole heap of stuff (well, it looks like it's doing *something* right!) until it comes to the last line which reads:
*E: Some index files failed to download, they have been ignored, or old ones used instead.*

I also get the same error message, as detailed above...

---

### Post by lodravah on 2006-05-10
I'm sorry, but I don't know what that is all about.. I went into source.list and #'ed the deb.-link and ran "sudo apt-get update" and now it works. Did you try all that the other dude wrote to help me?

lodravah

---

### Post by CybaCowboy on 2006-05-10
[QUOTE=lodravah][http://ubuntuforums.org/showthread.php?t=173363](http://ubuntuforums.org/showthread.php?t=173363)

I got the same error message. It seems that the link is dead and is pointing to the "Listen"-program for Gnome. I went into source.list and put the "#" in front of the link and the message went away. But check out the link i pasted, 'cause it is to my own post with the same problem. I got help, and now I hope I'm helping you..

lodravah[/QUOTE]

Sorry, I posted my link just after you posted your's, so I didn't get the message right away.

Anyway, I did the trick found at that link and it worked a charm... Sorta.

I don't get the above error message in Synaptic anymore, but when I do apt-get update I am told:
[i]E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory[/i]

---

### Post by lodravah on 2006-05-10
I'm not sure what it means, I'm afraid. I'm as new to this as you :P But I got help, so just keep asking. It's the only way to learn.. Good luck..

hvard

---

### Post by CybaCowboy on 2006-05-10
[QUOTE=lodravah]I got help, and now I hope I'm helping you..

lodravah[/QUOTE]

And *that's* where Linux **really** shines over Windows - the peer-to-peer support is fantastic, and far greater than I ever could have imagined!

---

### Post by lodravah on 2006-05-10
Let's just both of us get better at this, and then we can also help others.. A bit steep learning curve, but it can only go upwards!

lodravah

---

### Post by CybaCowboy on 2006-05-10
[QUOTE=CybaCowboy]Sorry, I posted my link just after you posted your's, so I didn't get the message right away.

Anyway, I did the trick found at that link and it worked a charm... Sorta.

I don't get the above error message in Synaptic anymore, but when I do apt-get update I am told:
[i]E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory[/i][/QUOTE]

Being the genius that I am, I was forgetting to type "sudo"...

Add that to apt-get update and it works fine.

My wonder Linux machine is now working absolutely perfect!

---

