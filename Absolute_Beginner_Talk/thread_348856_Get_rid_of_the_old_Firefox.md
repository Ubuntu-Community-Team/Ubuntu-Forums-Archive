---
title: "Get rid of the old Firefox?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by cairnsww on 2007-01-29
I have upgraded my Firefox to v2 using the excellent script available through the forums. (installnewfirefox.sh  2.14). It works like a dream. But now I suddenly get the problem that the update manager wants to "update" to v1.5. 

No No. Don't want to do that. (Even if it does not do any harm, do I really want to download 8 meg just to do no harm?)

I see how I can say, "No not now." Been there done that. But it keeps on thinking that it ought to remind me. How can I tell it, "No not now or ever?" 

Or is it that I really only have one version of Firefox intalled and it is just Synaptic that is confused?

---

### Post by jvc26 on 2007-01-29
The version in the repositories is 2.0.x if I remember correctly - what version of Ubuntu are you running as Firefox 2 is as standard in Edgy.
Il

---

### Post by cairnsww on 2007-01-29
Sorry - I should have mentioned that I am running Dapper. The standatd version of Firefox seems to have just become 1.5.

---

### Post by Frank Golden on 2007-01-29
> **cairnsww said:**
> Sorry - I should have mentioned that I am running Dapper. The standatd version of Firefox seems to have just become 1.5.What do you mean "the standard version of Firefox seems...."?.  

Is this the method you used to install FF2.0?

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

This is a great automatic update method by the way.

Anyway I have let Synaptic auto update my FF and it did not revert to the earlier version.
I would not uninstall the 1.5 version through synaptic. I read a warning,

see warning here

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

that removing the "Ubuntu" version of Firefox will break your machine.

---

### Post by cairnsww on 2007-01-29
> 

Is this the method you used to install FF2.0?

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Yes - and I took the warning to heart that I should not uninstall the previous version of Firefox.

> 
Anyway I have let Synaptic auto update my FF and it did not revert to the earlier version.

So what did it do - it could hardly upgrade version 2 to 1.5 :confused: 

Thanks very much for your help.

---

### Post by aysiu on 2007-01-29
When you use that script (or the Wiki instructions or Automatix), you actually have two versions of Firefox installed--but the Ubuntu one is inactive. So Synaptic wants to update the Ubuntu one. This has no effect on the Mozilla one.

The two are separate.

The command *firefox.ubuntu* will launch Ubuntu's Firefox (1.5). The command *firefox* will launch Mozilla's Firefox (2.0).

---

### Post by cairnsww on 2007-01-29
Thanks -

So is there any point in updating a version of Firefox that I am not using?

And, if not, how can I tell update manager to forget it?

---

### Post by aysiu on 2007-01-29
You can [lock the package version](http://ubuntuforums.org/showthread.php?p=2076216#post2076216).

---

### Post by cairnsww on 2007-01-29
Thanks - this is just what I was looking for.

Isn't it a bit ironic that exactly the same question was being asked on two different forums (this and General Help)? When I did a search to see if the problem had already come up, I did not see the other thread at all.

---

### Post by Frank Golden on 2007-01-30
Thank you aysiu for clarifying and the tip on locking versions.

---

