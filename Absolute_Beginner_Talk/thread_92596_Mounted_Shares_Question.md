---
title: "Mounted Shares Question"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by Stormspace on 2005-11-19
I cannot navigate through the filesystem to any mounted shares on my box. For instance a mounted share "Music" sitting on my desktop cannot be accessed via

cd /home/username/Desktop/Music

It is also not available to any app that includes a file browser. 

Does that mounted share exist elsewhere?

Also on the mounted shares I get prompted for a userid, domain, and password. I can fill in the information, but the prompt keeps coming back. If I click cancel the share opens and displays the contents fine. Do I need to change a config file somewhere to to keep this from happening.

I'm using a Peer tp Peer network, not a network with a domain, but I DID boot this PC onto a domain during part of the setup process.

---

### Post by Stormspace on 2005-11-20
I'm still kinda hanging out here. I don't guess anyone knows this answer or where it might be?

---

### Post by apjone on 2005-11-20
If you have just connected it via Places > connect to server , then they are in a hidden gnome folder in your home folder.

---

### Post by Stormspace on 2005-11-20
Yes. I've set them up that way and none of my apps except soundJuicer can see them.

---

### Post by apjone on 2005-11-20
in your home folder , press ctrl + H and look in the files starting .gnome

---

### Post by Stormspace on 2005-11-20
Did that. Lots of stuff there but no hooks into the FS of the shares.

---

