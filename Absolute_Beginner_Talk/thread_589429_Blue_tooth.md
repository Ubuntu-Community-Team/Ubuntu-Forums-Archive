---
title: "Blue tooth"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by EvilBro on 2007-10-24
I do not have any blue tooth devices nor do I expect to own them in the near future. Yet my computer runs a blue tooth applet (if I am not mistaken) and I have a 'wanting' to disable that. Two questions:

1. Should I, or should I just leave it alone because I might otherwise break things?

2. If I 'should', the next question is how? (is there a package I can disable or is there a service I should kill?)

---

### Post by realvz on 2007-10-24
goto application->system->services and uncheck the bluetooth service from there

---

### Post by EvilBro on 2007-10-24
> **realvz said:**
> goto application->system->services and uncheck the bluetooth service from there
It isn't checked, but the system monitor does show bluetooth-applet.

---

### Post by P4man on 2007-10-24
system -> preferences -> bluetooth preferences.

Uncheck all services (if any) and on the second tab you can hide the BT 'icon'.
By default, it should only show when it detects a BT adapter, are you sure you don't have one ? Or do you mean you don't have any BT devices other than your laptop that has BT radio built in ?

---

### Post by EvilBro on 2007-10-24
> **P4man said:**
> system -> preferences -> bluetooth preferences.
Now why oh why didn't that register in my brain when I looked at the preferences menu...

> By default, it should only show when it detects a BT adapter, are you sure you don't have one ?
Pretty sure. I haven't got any documentation that suggest my desktop has anything to do with Bluetooth and the hardware information doesn't mention anything that looks like BT.

On the second tab 'hardware database' is checked. Is that relevant?

---

### Post by P4man on 2007-10-24
No, that doesnt matter,I believe  it relates to the BT type of hardware (like headset, laptop, etc).

Another thing you could check is system / preferences / session. Possibly bluetooth manager is in that list, so it automatically starts. Remove it there if you don't want it to.

---

### Post by gecko_gp on 2007-10-24
i have bt on my laptop, but when im not using it i want to turn it off??? is this posible???

---

### Post by P4man on 2007-10-24
most laptops have a key for this. either a dedicated button, or Fn+some function key combination. On my laptops that still works under Ubuntu as well, it just turns off the radio (saving some battery power). Can you not turn off your BT radio with your keyboard ? What laptop do you have ?

---

### Post by gecko_gp on 2007-10-24
i have a dell inspiron 6000. it has a button but it turns of the wireless and the bt, and i just want to turn off the bt :confused:

---

### Post by P4man on 2007-10-24
Try this:

sudo /usr/sbin/hciconfig hci0 down

It may or may not turn off the BT light, but it should turn off the radio. To turn it up again

sudo /usr/sbin/hciconfig hci0 up

---

### Post by gecko_gp on 2007-10-24
thanks

---

