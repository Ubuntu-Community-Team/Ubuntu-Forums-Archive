---
title: "How would you go about this....(my brain has melted)"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by blop on 2007-11-23
HI all,

i need to setup permissions to share a folder that i have on ubuntu with the network but limit access to a specific user, but i have confused myself thinking about it.

My downstairs pc is open access so auto logs in with an account called User, now i have setup another user called Private and made a folder with that account to keep some files in that only Private can access. On the folder tab i have disabled any access or read right access to anyone who is not the owner.

But...

I now want to share that folder over the network and let only 1 specific account access it...

can anyone help?

Basically i want to backup My Docs from my XP machine to my trusty feisty and just curb access to anyone....other than me..

---

### Post by Dr Small on 2007-11-23
Are you planning to use Samba to access "Private"'s files over the network ?

---

### Post by blop on 2007-11-23
sorry....did not expect such a quick reply...thank you

Yes i was planning on using samba....i have it already setup...but this folder with the fact its private confuses me how im gonna share it. The rest of my samba shares are open to all with the line..

secruity = share


cheers!

---

### Post by blop on 2007-11-25
bump o matic

---

### Post by blop on 2007-11-25
bumpo

---

### Post by bluepowder7 on 2007-11-25
no idea, but i'll throw out a thought - can you use symlinks for this somehow?

---

### Post by bettermentflux on 2007-11-26
The secret is found in /etc/samba/smb.conf

I believe I used the Red Hat guide to configure mine. Try this page: [http://kbase.redhat.com/faq/FAQ_71_2356.shtm]("http://kbase.redhat.com/faq/FAQ_71_2356.shtm")

---

