---
title: "Unexpected outgoing traffic"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by SteelDragon on 2007-10-21
Hello all.

I've got Feisty running with KDE core. All weekend my conky has been telling me that I'm uploading over 100 k/s from eth0, even when I've got no apps running that should be doing that. I've tried unplugging the modem to make sure that conky is actually reading something real, and it dropped off immediately. About ten minutes after reconnecting, I'm uploading like a bandit again.

I have to assume that this is abnormal, since I've been on (K)Ubuntu for about 8 months now and have never seen it. Any way I can stop it (short of unplugging) or at least see what it is and where it's going? 

Thanks

SteelDragon

PS I don't know at what point I stop being an "absolute beginner", but I figured this was the appropriate forum since it's a "WTF Please Help I'm Confused" type of question.

---

### Post by misfitpierce on 2007-10-21
firestarter firewall program can show current open programs running traffic. Can try using that.

sudo apt-get install firestarter

---

### Post by SteelDragon on 2007-10-21
Excellent. Thanks alot.

It was that sneaky rtorrent running in the background.
Know how I can re-open my running rtorrent session after restarting X, instead of just starting a new one, which is apparently what I've been doing?

---

