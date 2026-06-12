---
title: "Thunderbird links to firefox??"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by DoorGunner on 2006-01-04
Hi

I am having a bit of trouble with thunderbird. When i click on an email link it opens up firefox as it should. However, It will only go to my home page. 

What can i do to get the appropriate link to open?

I use firefox1.5

---

### Post by audax321 on 2006-01-04
I actually have the same problem on my desktop at home. My laptop opens Firefox and goes to the correct address. But my desktop only loads the homepage like yours. I haven't been able to figure out why.... :confused:

But, I'm using Firefox 1.0.7...

---

### Post by Lord Illidan on 2006-01-04
Hmm, mine doesn't link at all. Is it because I have firefox 1.5? How do I link them together?

---

### Post by DoorGunner on 2006-01-04
Sorry. I seem to be answering my own problems. I spent several days on this and I found an importantthunderbird faq clue.

what i did was the following.

in root or you can sudo as ubuntians like to do


> 
sudo  gedit /etc/mozilla-thunderbird/global-config.js


you will see the following

*/
 // pref("network.protocol-handler.app.http","mozilla-firefox");
 // pref("network.protocol-handler.app.https","mozilla-firefox");

You need to un-hash it and remove mozilla so that i looks like this.

*/
 pref("network.protocol-handler.app.http","firefox");
 pref("network.protocol-handler.app.https","firefox");

by removing the hash marks it activates the line and you might see it change script color. 
I think what happened is this.
When we added the origional firefox with synaptic or apt-get it came with a mozilla-firefox start. Now that we have a generic firefox .bin download that changed it to firefox not mozilla-firefox. There may have been some residual scripts that were left to interfere with the links. 
Just my thought on it. Actually audax you could try just unhashing or you could try changing removing the mozilla too. it might just work for you.

---

### Post by Lord Illidan on 2006-01-04
Nice work. Now I can ease off the copying and pasting slashdot links in firefox.. if only it can load a little faster.

---

