---
title: "Can't seem to stop all screen tearing"
date: 2014-07-01
forum: Any Other OS
---

### Post by buntumax on 2014-07-01
I don't have tearing in Vlc or Xbmc but eveywhere  else I do in all online videos when I move windows and games and I tryed  the etc/environment fix but no luck. Can anyone help me on this?

---

### Post by deadflowr on 2014-07-01
Give us all the info you can
Which mint (cinnamon, mate, other) and which mint version (16, 17, other)?
What's the graphics card?
Which programs do this tearing?

That should  be a good starting point.

---

### Post by buntumax on 2014-07-02
> **deadflowr said:**
> Give us all the info you can
Which mint (cinnamon, mate, other) and which mint version (16, 17, other)?
What's the graphics card?
Which programs do this tearing?

That should  be a good starting point.


Thank you for the replay I am using Mint 16 and Mate my graphics card is Nvida GeForce GT 440. I get tearing in all online videos unless I use xmbc, most games and when I move windows from side to side.

---

### Post by deadflowr on 2014-07-02
Are you using the open-source drivers or did you install nvidia drivers?
If you install the nvidia drivers, do you know which ones?
Or from where(either the .run file from nvidia or through software center/whatever mint uses)?

---

### Post by buntumax on 2014-07-02
> **deadflowr said:**
> Are you using the open-source drivers or did you install nvidia drivers?
If you install the nvidia drivers, do you know which ones?
Or from where(either the .run file from nvidia or through software center/whatever mint uses)?


I am using the Nvidia-319 proprietary drivers and got them though the Driver Manager.

---

### Post by deadflowr on 2014-07-02
I'm guessing you looked into the nvidia control panel program "nvidia X server settings", or whatever it is called on mint.
Is sync to vblank enabled, or disabled.
(I think it should be under OpenGL settings, or something like that)
Maybe try toggling the option and see what the result is.
Might need to reboot for it to take effect.
If it results in a worse state, then re-toggle it back.

---

### Post by buntumax on 2014-07-02
> **deadflowr said:**
> I'm guessing you looked into the nvidia control panel program "nvidia X server settings", or whatever it is called on mint.
Is sync to vblank enabled, or disabled.
(I think it should be under OpenGL settings, or something like that)
Maybe try toggling the option and see what the result is.
Might need to reboot for it to take effect.
If it results in a worse state, then re-toggle it back.



In nvidia X server settings with sync to vblank seems to have no effect.

---

