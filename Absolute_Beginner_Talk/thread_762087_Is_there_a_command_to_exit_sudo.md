---
title: "Is there a command to exit sudo?"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-04-21
Is there any command that will make you reenter your password besides waiting for the time to run out once you've already entered it with sudo <command>?
I know how to use visudo to edit the timestamp but I'd rather be able to manually close my superuser session with a command if possible.

---

### Post by amingv on 2008-04-21
```
sudo -k
```

---

### Post by mgranet on 2008-04-21
Not that I'm aware of. There is a way to set a root password and just use su, if you prefer to do it that way.

---

### Post by mgranet on 2008-04-21
> **amingv said:**
> ```
sudo -k
```

And I stand corrected. Thanks, **amingv**.

---

### Post by stchman on 2008-04-21
> **garyed said:**
> Is there any command that will make you reenter your password besides waiting for the time to run out once you've already entered it with sudo <command>?
I know how to use visudo to edit the timestamp but I'd rather be able to manually close my superuser session with a command if possible.

If you mean you want to enter your password on each sudo command just close the terminal you entered the sudo command in.

Open up another terminal and you will be prompted to enter password for sudo commands.

The timer is right around 5 minutes so it should be a non issue.

---

### Post by philinux on 2008-04-21
> **mgranet said:**
> Not that I'm aware of. There is a way to set a root password and just use su, if you prefer to do it that way.

More than one way to skin a rabbit.

Option

Use su then exit or ctrl d to quit the su session

---

### Post by mgranet on 2008-04-21
> **philinux said:**
> More than one way to skin a rabbit.

Option

Use su then exit or ctrl d to quit the su session

Wait a minute. You mean I can use su, *without* setting a root password??

---

### Post by amingv on 2008-04-21
> **mgranet said:**
> And I stand corrected. Thanks, **amingv**.

You're welcome. :)
It's a good thing to know when you have a nose over your shoulder who wants to "Do something real quick", or to put at the bottom of upgrade scripts.

---

### Post by Joeb454 on 2008-04-21
Actually from what I'm aware the timeout on sudo is more like 15 minutes

---

### Post by garyed on 2008-04-21
> **amingv said:**
> ```
sudo -k
```


Exactly what I needed.
Yhanks again

---

### Post by bodhi.zazen on 2008-04-21
> **mgranet said:**
> Wait a minute. You mean I can use su, *without* setting a root password??

yes, 

sudo su

---

