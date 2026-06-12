---
title: "Wireless problem in Ubuntu with some cards."
date: 2009-07-19
forum: Apple Hardware Users
---

### Post by volanin on 2009-07-19
Hello,

Recently I discovered a problem in my Ubuntu Jaunty installation in my
Macbook 2,1. The Macbook uses an Atheros cards and for some reason the
network completely stalled for 1 to 5 seconds every 2 minutes exactly.

I mean, if I was downloading something, the speed would fall to 0kb/s
for 1 to 5 seconds and then everything would return back to normal.
But this was enough to give me a bad experience in sites such as
YouTube and Skype.

After searching around A LOT, I found out that Network Manager scans
for new networks every 2 minutes and this causes some wireless drivers
to stall, one of them being our beloved ath9k.

I have created a patch to work around this problem in Network Manager.
Basically, the patch stops Network Manager from scanning for new networks
if you are already connected. This means that the network won't stall
anymore, but this also means that you won't have an updated list of
access points while connected.

If you think that your wireless connections is not so good in Jaunty,
you can give this patched Network Manager a try.
It solved the problem for me.

Bug Report:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/373680](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/373680)

Patched Network Manager:
[https://launchpad.net/~volanin/+archive/ppa](https://launchpad.net/~volanin/+archive/ppa)

[i]Warning: Please do not add this PPA to your source file, since some
packages there are experimental and might ruin your experience.
Just download what you need ok![/i]

That's it.
:)

---

