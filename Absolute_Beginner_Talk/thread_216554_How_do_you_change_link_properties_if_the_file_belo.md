---
title: "How do you change link properties if the file belongs to root?"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by southerngrey on 2006-07-15
I am trying to fix a bug in which a link for a ACX-111 module is directed to the wrong folder. Can anyone tell me how to change the link properties please?

---

### Post by Swab on 2006-07-15
Can you elaborate further... if you need to change something that belongs to root, you can use the sudo command.

See here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by southerngrey on 2006-07-15
There is a bug for ACX-111 cards that the default link for the firmware is to the wrong location.  ref: [http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)
I have found the link but am unsure how to change it's target. I can't seem to do it in X and my terminal is fairly limited. I presumed I couldn't adjust it as it belongs to root?
Cheers

---

### Post by Swab on 2006-07-15
So I guess you could delete the old link, then create a new one as follows..

```

rm *path to old link*
ln -s *path to target linkname*

```

---

### Post by southerngrey on 2006-07-15
That certainly put the link there, thanks very much.  Now just got to test if it gets the network working with the new kernel.  much appreciated.

---

### Post by southerngrey on 2006-07-15
Wireless now working with new kernel - fantastic.  I have been working on this for three days now.  Thanks very much, only a little thing but made a huge difference.  I will post the solution on the wireless sections, Other newbies were having trouble with this as well.  Have a good day.

---

