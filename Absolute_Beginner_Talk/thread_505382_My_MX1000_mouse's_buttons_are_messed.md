---
title: "My MX1000 mouse's buttons are messed"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by bollofinwe on 2007-07-20
Hey guys,

Here's the problem:

My Logitech  MX100 mouse's side buttons are not configured correctly. The button which is meant to go back in Firefox is configured to clocking the scroll wheel in and the button which is meant to go forward is configured to right clicking.

How would I go about correcting this?

I followed another guide which told me how to configure all buttons but it stopped my scroll wheel from working and I had to reinstall ubuntu to fix it so please don't link me to that again.

Any help will be highly appreciated,

Thanks,

Bollo

---

### Post by linuxwizard on 2007-07-20
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

### Post by bollofinwe on 2007-07-20
> **linuxwizard said:**
> [https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

Yeah, thanks for the link. But now my back button is assigned to alt and left as opposed to the actual button and forward alt and right.

Moving the scroll wheel left and right is now assigned to these buttons. Mouse wheel left is back button mouse wheel right is forward.

Also, how would I bind the middle side button to the scroll wheel click in?

---

### Post by bollofinwe on 2007-07-20
Hmm, looks like I fixed it. Just changed the line:

```
Option          "HWHEELRelativeAxisButtons" "7 6"
```

to:

```
Option          "HWHEELRelativeAxisButtons" "9 8"
```

This changed the bind from my mouse wheel sidewards to the side buttons.

Dont know WHY this fixed it but it seems messing about until it works is good.

Anyone know how to bind my side middle button to clicking in the mouse wheel?

I tried using xbindkeys and typing in this:

```
"/usr/bin/click 2"
  b:10
```

As button 10 is the side button and click 2 should be clicking in the mouse wheel. Just a guess however it didn't work.

Any ideas?

---

