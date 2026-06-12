---
title: "Add fish plugin to xchat?"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by akkabuto on 2006-02-13
Hi!

I'm trying to add the fish addon for xchat. It says that I should put xfish.so under xchat plugin directory. /usr/lib/xchat/plugins/ is the directory I try to extract the file to.

But I only get an error that I don't have the privilige to extract the file into that folder. I don't know how I should get access to that folder, because I wasn't asked to create a pwd for root account or something like that under the installation. So the only account I have is this one.

I'm a totaly newbee to this so please help me out!

Best regards /Akka

---

### Post by Kimm on 2006-02-13
you should put 'sudo' before the command you use to copy the file

```

sudo cp xfish.so /usr/lib/xchat/plugins/

```

sudo will ask for YOUR password, the same password that you use to login.

---

### Post by akkabuto on 2006-02-13
Thank you Kimm. It worked like a charm!

Beest regards /Akka

---

### Post by Kimm on 2006-02-14
happy it worked out for you :)

---

