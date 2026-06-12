---
title: "Installing on Raid 0 (fakeraid?) -  ASUS CROSSHAIR AM2 NVIDIA nForce 590 SLI MCP"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by osc1882 on 2008-02-16
I just bought a  ASUS CROSSHAIR AM2 NVIDIA nForce 590 SLI MCP and I wanted to set up XP and ubuntu on a raid 0 of two hard drives. I set up XP and I went to go install Ubuntu to find out that this is much harder then I thought it would be.
I read that this is a "fake raid" that is mostly software based and this is the reason that ubuntu can't handle this out of the box, is this true?

I first tried following this guide:
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

It seemed to be working untell I got to the line:
apt-get install ubuntu-base linux-386 ubuntu-desktop dmraid grub
I can't remember what error it dished out at me because it was late, 4am.  And I clearly could not move on because this adds grub to the install. 
But I had a question about this guide, if both grub and ubuntu does not have support for fake raid out of the box then how does grub load even following these instructions. 

I then read that I could use the Alternative cd install. So I downloaded and burned that. But I read later on that this just ads it's own form of software based fake raid outside of the fake raid that the mother board uses. So am I right to understand that, that means that I could not use windows and ubuntu on the same box if I did this?

Am I right to understand that I couldn't install windows on the raid and not ubuntu because grub would have to be on the same raid as the windows drives and grub can't take fake raid?

How much gameing ( and other ) performance would I be missing by not useing raid all together?

Thank you for your time. I hope someone can help.

---

### Post by badmedic on 2008-02-16
Have a look at this guide:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I think it is a bit more detailed. Hope it helps!

---

