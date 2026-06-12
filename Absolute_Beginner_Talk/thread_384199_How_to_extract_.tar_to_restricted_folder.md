---
title: "How to extract .tar to restricted folder?"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by philipho on 2007-03-14
Hi,

I have cairo-dock.tar.gz on my desktop, however, when i try to extract it to /opt, i get access denied errors.

May i know how can i extract it to /opt?

---

### Post by hyper_ch on 2007-03-14
in a terminal run

> 
sudo tar xvfz cairo-dock.tar.gz /opt/


---

### Post by reverend_HH on 2007-06-07
i tried the above suggestion but i get the following message:

tar: /opt: Not found in archive
tar: Error exit delayed from previous errors

---

### Post by shirilover on 2007-06-07
the command is missing a switch. try
```

sudo tar -xzvf cairo-dock.tar.gz -C /opt

```

---

### Post by Hendrixski on 2007-06-07
> **shirilover said:**
> the command is missing a switch. try
```

sudo tar -xzvf cairo-dock.tar.gz -C /opt

```

right, because you probably don't have an /opt folder to begin with, so you need to have it created.

---

