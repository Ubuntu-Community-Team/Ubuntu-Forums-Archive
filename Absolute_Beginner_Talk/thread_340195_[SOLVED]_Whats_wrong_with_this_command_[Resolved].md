---
title: "[SOLVED] Whats wrong with this command [Resolved]"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-01-16
This is from a guide to put /home on its own partition. All went well till copying to the new directory then it says cpio is missing something.  Can someone tell me what.

Since the “/home” directory will have hardlinks, softlinks, files and nested directories, a regular copy (cp) may not do the job completely. Therefore, we use something we learn from the Debian archiving guide:

$cd /home/
$find . -depth -print0 | cpio –null –sparse -pvd /mnt/newhome/

Make sure everything copied over correctly. You might have to do some tweaking and honing to make sure you get it all right, just in case.

Thanks

---

### Post by taurus on 2007-01-16
Are you using this guide, especially the section on [COLOR="Red"]Using the new partition[/COLOR]?

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by squrl on 2007-01-16
Thats where it started out but it ends up at the ubuntu blog where you can do this with an already installed ubuntu.          (ubuntu word press .com)

---

### Post by aysiu on 2007-01-16
I'm not sure what you mean about starting and ending.

I wrote the Psychocats tutorial and based it almost entirely on the Wordpress one.

It is the **same** tutorial--just presented in a different way.

One does not end anything that the other started. They are the same tutorial--beginning to end.

---

### Post by squrl on 2007-01-16
About half way through it says go "here" if you want to do this after ubuntu is installed. Thats where I get to ubuntu blog

It doesn't make any difference.  All I want to know is what is wrong with the syntax of the command. 

Thanks       I think I just figured it out

---

### Post by bodhi.zazen on 2007-01-16
You have a small typo :p

Should be:

```
find . -depth -print0 | cpio –-null –-sparse -pvd /mnt/newhome/
```

That is TWO (2) - in front of BOTH null and sparse.

In some browsers the -- (doubble dash) is converted to a single dash

8)

Ah, I see you got it as I typed :)

---

### Post by squrl on 2007-01-16
Thanks.  It took a magnifying glass to see it and a hammer to get it in my head but finally got there.

---

### Post by bodhi.zazen on 2007-01-16
"There's no place like home" ....

Hope your move went OK :p

When is the house warming party ?

---

### Post by squrl on 2007-01-16
Thank you Thank you.   The move was a total success. My /home is now on a separate "partition and drive"

---

