---
title: "NTFS and Linux"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by usarmykr on 2007-10-21
OK, Ive got a question. I am dual-booting because windows SLI is 10 times better than Linux SLI for the moment. I get all my games working in linux, but have better performance in windows, so I dual boot. I just reinstalled windows and linux, and notice that I can read and write to my "data" partition which is formatted as NTFS. How reliable is this writing? I know that reading NTFS has been fine for awhile, but not sure on the writing aspect, last post I can find here is almost a year old. I read on ntfs-linux.com(org maybe) that the NTFS read/write driver is included in the kernel now. Can I install games, like WoW into my NTFS partition and play them with wine? Or does wine have certain dependencies? Does anyone have any experience with this? Just want to know, in case I am doing something in linux and want to play a quick game of something. If anyone knows anything about this, let me know please. Thanks in advance for the help :P

---

### Post by chessercizes on 2007-10-21
hey

NTFS read/write is fully stable now!! :KS

about the second, i'm really not sure. I'm using gutsy and installed wine via the repositories, so that took care of all the dependencies. I don't see why it shouldn't work to play WoW off of your NTFS drive, but i guess try and see =)

best of luck =)

---

### Post by usarmykr on 2007-10-21
Well what I meant to ask was does wine have a registry like windows?  I know wow has no reg entries so you can play it off a thumb drive if you want (Ive played it off an ipod before lol) will it work for other games as well?

---

### Post by usarmykr on 2007-10-21
and also do I need any additional packages, or is the NTFS support built in already.

---

### Post by Maestro23 on 2007-10-21
> **usarmykr said:**
> and also do I need any additional packages, or is the NTFS support built in already.

If you're running 7.10, it's there by default. You will need the ntfs-config though.

> sudo apt-get install ntfs-config

*Once installed, it will be an entry on your menu. I think Apps>> System Tools

---

### Post by usarmykr on 2007-10-21
@ Maestro23

You don't happen to know if my installed games in windows will work under wine when I am in linux?

---

### Post by Maestro23 on 2007-10-21
> **usarmykr said:**
> @ Maestro23

You don't happen to know if my installed games in windows will work under wine when I am in linux?

Games running under Wine are a case-by-case basis.  You will need to check the Apps Database over at WineHQ for all your games.

WineHQ: [http://appdb.winehq.org/](http://appdb.winehq.org/)

*I'm a heavy gamer and that is the only reason XP is still on my system.

---

### Post by usarmykr on 2007-10-21
> **Maestro23 said:**
> Games running under Wine are a case-by-case basis.  You will need to check the Apps Database over at WineHQ for all your games.

WineHQ: [http://appdb.winehq.org/](http://appdb.winehq.org/)

*I'm a heavy gamer and that is the only reason XP is still on my system.

OK so wine shouldnt have an issue running supported games from the NTFS partition?

---

