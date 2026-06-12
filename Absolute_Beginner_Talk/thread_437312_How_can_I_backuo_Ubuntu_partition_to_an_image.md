---
title: "How can I backuo Ubuntu partition to an image?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-08
Basically, I shot myself in the foot.

I backed up Ubuntu with Norton Ghost 2003 and restored it today.  Unfortunately, it was all errors and would not boot, so I am now reinstalling.

How can I backup Ubuntu to avoid this in the future?

---

### Post by aysiu on 2007-05-08
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by bodhi.zazen on 2007-05-08
1. ALWAYS TEST you back up image :)

2. I like partimage a lot, although there are other options ...

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by hyper_ch on 2007-05-08
You could use dd

```

sudo dd if=/dev/hdX of=/media/backup/DD_BACKUP

```

---

### Post by gohanssjn on 2007-05-08
For some reason I get an operation failed: Premission Denied with dd-rescue :(

Everything is unmounted.  What am I doing wrong?

---

### Post by gohanssjn on 2007-05-08
I cannot seem to get anything to make an image.  I am at a pint that I want a good reliable backup of this.

What would help you all help me?

---

### Post by bodhi.zazen on 2007-05-08
> **gohanssjn said:**
> I cannot seem to get anything to make an image.  I am at a pint that I want a good reliable backup of this.

What would help you all help me?

Hmm ...

Error message ?

What are you using to try to make a back up ?

Make backup from a live CD ! 

That way you can unmount the root partition :)

HTH

---

### Post by gohanssjn on 2007-05-08
GOT IT.

I was on the LiveCD, but apparently hadn't mounted the /backup dir, because I was skipping images and following text.  BIG mistake, lol.  Thanks all!

---

