---
title: "permission problem"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by wana10 on 2007-07-08
interesting dilemma here that I have never had before. everything was going fine, no problems until *bam* disaster struck. i left for work today leaving my computer in the middle of a process and while at work my house must have had a brief power outage. now i'm protected by a surge protector so no worries there, and after rebooting my system seemed ok. then i tried to plug in my usb flash drive. the comp thought for a moment and spat out an error message saying i don't have permission to mount the flash drive:confused: i had always mounted and used it prior to this, what was different now? so i tried my psp, plugged it in, selected usb mode, and there was the same error message. starting to get worried i went to back up some important data to my external harddrive, only to find that i no longer had write permission to that folder and nothing i could do would change that fact. i ended up having to command line 'sudo cp' everything i wanted to back up.

if anyone knows what in blazes happened and how to fix it i would be most appreciative, thanks for your time.

---

### Post by ajmorris on 2007-07-08
you could make your user the owner of the usb drive, so sudo chown *user* /dev/usb1

or you could give everyone read write and execute by sudo chmod 777 /dev/usb1
or just everyone read & write while leaving ¨other¨ default would be sudo chmod 775 /dev/usb1

---

