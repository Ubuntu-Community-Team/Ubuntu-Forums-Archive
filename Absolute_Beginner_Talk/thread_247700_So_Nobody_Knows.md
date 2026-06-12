---
title: "So Nobody Knows ?"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-08-31
How to make a proper source list ?? I can't beleive it !!! Sorry,but 5 pages back now from: [http://www.ubuntuforums.org/showthread.php?t=247444](http://www.ubuntuforums.org/showthread.php?t=247444)
And still no reply ??..........................

---

### Post by Carbonfish on 2006-08-31
Drakkor,

I don't know what went wrong for you regarding the copy/paste process of the sources list, but it went fine for me.

What I would suggest is, going back to that thread, copying the source list form the link that HymnToLife provided and after deleting the contents of your /etc/apt/sources.list 
paste the source list into that empty file.

Then run sudo apt-get update.

One thing. Although it shouldn't make any difference, you don't need the duck story at the top of the list. All of that stuff at the top that is commented out you can omit from what you copy.

I followed the steps that HymnToLife suggested and had zero problems. 

If you are wondering from "where" to paste the sources list, it should have been copied to your clipboard (or whatever it's called in Linux), so unless you have copied other stuff, it should still be there.

KC

---

### Post by aysiu on 2006-08-31
If you want a fresh list, try this:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by omns on 2006-08-31
.

---

### Post by Drakkor on 2006-08-31
Thanks , guys I'll try all that.one question? I don't understand all the commented out entries,aren't they just superfluous ?? As in they really don't matter at all ?? Sorry noob.  :-k

---

### Post by pyros on 2006-08-31
No, they don't affect the functionality at all.

---

### Post by Carbonfish on 2006-08-31
> **Drakkor said:**
> Thanks , guys I'll try all that.one question? I don't understand all the commented out entries,aren't they just superfluous ?? As in they really don't matter at all ?? Sorry noob.  :-k

Generally, the "commented out" parts are either a preview of coming attractions (an explanation of what the following lines represent or do), or they are just what they seem... comments.

The reasons that they are commented out may vary, but the result is  that Linux (UNIX) won't see them if they have a # in front of them.

For instance, if you want to change a file so that it behaves differently, but don't want to completely remove the line so that you know what and where it was, you can just comment it out and it becomes invisible to the OS.

KC

---

### Post by angkor on 2006-08-31
second time I paste this link in 15 minutes :)

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by aysiu on 2006-08-31
Are you pasting that link into your web browser address bar?

---

### Post by angkor on 2006-08-31
> **aysiu said:**
> Are you pasting that link into your web browser address bar?

What do you mean? Wether I paste it from my adress bar? Yes...I can't remember anything ;) Linked to that site on another thread with a similar problem as well.

---

### Post by aysiu on 2006-08-31
I'm sorry--so what's the problem? You said you pasted the link twice. Did the webpage not come up? Did it not generate a sources.list for you?

---

### Post by angkor on 2006-08-31
> **aysiu said:**
> I'm sorry--so what's the problem? You said you pasted the link twice. Did the webpage not come up? Did it not generate a sources.list for you?

You lost me :) 

Why would there be a problem? I said I posted the link for the second time in 15 minutes (on ubuntuforums) because earlier I posted the link in a thread where somebody  had a corrupted sources.list too.

---

### Post by aysiu on 2006-08-31
Ah, now I get it! Thanks for the clarification.

---

### Post by angkor on 2006-08-31
You're welcome. :D

---

