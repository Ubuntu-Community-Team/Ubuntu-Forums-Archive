---
title: "Password Problem"
date: 2012-09-06
forum: Any Other OS
---

### Post by Adejoe1 on 2012-09-06
Hi there. I'm a newbie. I use Linux mint 13 Cinnamon. I don't know what I did, it must have been something pretty dumb as I can't install any app right now. Any time I tried to install any app thru the Software Centre, I am asked for a password. When I enter my password it says authentication attempt  unsuccessful, try again. Please how do I get round this problem. I am really enjoying this OS. Thanks.

---

### Post by Elfy on 2012-09-06
*Thread moved to **Other OS/Distro Talk**.*

Not sure why you started an account here - mint has it's own forum.

try this [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by shadedpixel on 2012-09-08
> **Adejoe1 said:**
> Hi there. I'm a newbie. I use Linux mint 13 Cinnamon. I don't know what I did, it must have been something pretty dumb as I can't install any app right now. Any time I tried to install any app thru the Software Centre, I am asked for a password. When I enter my password it says authentication attempt  unsuccessful, try again. Please how do I get round this problem. I am really enjoying this OS. Thanks.
When booting, and shown the grub screen. Choose the linux mint "(recovery mode)" option. Then choose “Drop to root shell prompt” from the menu that appears.

Then you should be able to use:
```
passwd [YOUR USERNAME HERE]
```

You will be prompted for a new password, enter one and confirm it. Then try installing from the Software Centre with that password.

Hope it helps.

---

