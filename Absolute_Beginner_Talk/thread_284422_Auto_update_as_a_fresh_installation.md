---
title: "Auto update as a fresh installation"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by englishmen on 2006-10-25
Tomorrow when 6.10 is released it will be my first ubuntu update(been using ubuntu for about 4 weeks now), I'm assuming it will be available via auto update, correct?

If so is it possible for it to install it like a fresh installation rather then a update?

Thanks

---

### Post by Jussi Kukkonen on 2006-10-25
Yes, it will be available. No, it won't be possible to do a "fresh install" -upgrade (you'll have to burn a CD).

EDIT: Just to alleviate possible upgrade-fears: If you haven't used 3rd party repositories or otherwise installed unknown apps, a new install such as yours *should* be a piece of cake for the upgrade-system.

---

### Post by englishmen on 2006-10-25
First off let me say i love this forum and and its users, everyone's polite and so far all my questions have been answered more or less immediately, keep it up.

Also thanks Jussi Kukkonen for answering my question.

---

### Post by thornomad on 2006-10-25
> **englishmen said:**
> First off let me say i love this forum and and its users, everyone's polite and so far all my questions have been answered more or less immediately, keep it up.

I second that!  Thanks everyone.

Am looking forward to the new release tomorrow too -- though I think I will burn a new CD and redo everything ... I have all my data files on a different partition and have already been playing so much with this install that I could use a fresh start.

---

### Post by englishmen on 2006-10-25
> **thornomad said:**
> Am looking forward to the new release tomorrow too -- though I think I will burn a new CD and redo everything ... I have all my data files on a different partition and have already been playing so much with this install that I could use a fresh start.

Exactly the same here.

---

### Post by Jussi Kukkonen on 2006-10-26
You decided to go with a clean install so this doesn't really  concern you. Still, a correction: I was wrong about the automatic upgrade notification. Apparently 6.06 does not automatically offer the upgrade to 6.10 as it is a "Long Time Support"-release -- you'll have to run:
```
gksu update-manager -c
```

---

### Post by raqball on 2006-10-26
That is correct! You will need to run the above command in terminal to upgrade to 6.10.

That might be a better option than the clean boot from CD as you will save a bit of time as opposed to having to download the ISO, burn it, boot live CD, and install...

The upgrade starts, you can pretty much walk away and come back in an hour or so and it should be complete. Reboot and done! Plus all your custom desktop setting will stay :)

---

### Post by englishmen on 2006-10-26
> **Jussi Kukkonen said:**
> You decided to go with a clean install so this doesn't really  concern you. Still, a correction: I was wrong about the automatic upgrade notification. Apparently 6.06 does not automatically offer the upgrade to 6.10 as it is a "Long Time Support"-release -- you'll have to run:
```
gksu update-manager -c
```

That code didn't work but the below did, how come i need ""?

```
gksu "update-manager -c"
```

---

