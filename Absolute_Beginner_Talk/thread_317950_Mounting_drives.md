---
title: "Mounting drives"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-13
Hello people , 
              I want to mount the /home directory of one of my ubuntu virtual machines to another ubuntu virtual machine . 

How do i go about doing this ?

---

### Post by Ben Sprinkle on 2006-12-13
```

sudo mount /home /pat

```
I have never done this but if you need mounting normal drives:
```

sudo mount /dev/sda1 /media/sda1

```

---

### Post by lance_klusener on 2006-12-13
These are virtual machines i am talking about , could you explain further since these machines are behind NAT

---

### Post by Ben Sprinkle on 2006-12-13
I do not understand, do you mean you are remote'ing into it?

---

### Post by lance_klusener on 2006-12-13
No this is the scneraio

1] There are 2 windows machines that i have on a lan 
2] These windows machines have ubuntu running virtually using VMWare 
3] Now i want to mount the home directory of one ubuntu machine into the other.

How do i do this ?

---

### Post by Ben Sprinkle on 2006-12-13
Hmm, you have to make a virtual lan in your vmware'd ubuntus. Much like normal ubuntu. Then mount it to the shared folder.

---

