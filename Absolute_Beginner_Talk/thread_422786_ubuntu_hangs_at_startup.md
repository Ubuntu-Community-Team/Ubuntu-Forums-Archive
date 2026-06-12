---
title: "ubuntu hangs at startup"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by leeg on 2007-04-25
Ok, so having had my pc successfully running using the live cd of feisty, I decided to do a clean install on my hard drive rather than to update what was on ther before which was edgy. All seemed to go ok until on the restart when the Ubuntu load screen with the bar underneath it just sits there with the having moved just a tiny bit. Any ideas:confused:  Thanks:)

---

### Post by marx2k on 2007-04-25
Have you tried this through multiple reboots?

You might need to edit your grub menu list and remove the 'quiet' modifier from your kernel loading line to see where it's pausing at during boot.

go to /boot/grub and edit menu.lst
Search for the word 'quiet' and remove it and try rebooting

I might be off a little on the exact location of that file since I am typing this from a liveCD while installing fiesty and the /boot directory doesnt even have a /grub directory in it as it didn't load from GRUB :)

---

