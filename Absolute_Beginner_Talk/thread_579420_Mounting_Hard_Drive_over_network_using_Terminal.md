---
title: "Mounting Hard Drive over network using Terminal"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by ZedMan on 2007-10-18
Been using Kubuntu 7.04 for a little while now (I know this is an Ubuntu forum, but I need to do stuff in the terminal so bare with me), I'm using it to stream media across my network to a projector I recently bought.

Yesterday, my housemate gave me his old USB TV tuner, and after a lot of frustration, managed to get it to work.

It's been on all night, as the same housemate was watching TV. It has had a reboot since the TV tuner has been installed, but when I turned it off this morning before I went to Uni, and went to turn it on again when I got back, I started to get some problems.

Firstly, X would not start. So I thought, fine, I'll reboot. On the reboot, I noticed that a file failed to load due to the hard drive being full, and the same thing happened with X not starting, so I'm assuming it didn't work because of that the first time.

Basically, I made this media streamer on the cheap, got a 6.4 gig hard drive, and when I use df -h, it says that /dev/hda1 is full.

There are files on there that I can delete, but I far prefer using a GUI to do so, as it's quicker etc. Also, it would be good in the future if anything like this happens again.

I can connect via SSH to this media streamer via my main computer. Now how do I make it so I can mount the hard drive on the media streamer to the main computer?

I'm hoping that if I can free enough disk space for X to start, I can then do the rest downstairs.

Thanks

---

