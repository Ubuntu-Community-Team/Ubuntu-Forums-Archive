---
title: "Wireless works now...well sort of..."
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-19
Well, after 4 days of tackling my wireless problems I finally had a breakthrough last night! I run a 64-bit system and someone mentioned in a post that the following command would work:


sudo apt-get install bcm43xx-fwcutter
then
sudo modprobe bcm43xx

sure enough after I ran it I opened my wireless assistant and it kicked right on and connected me to the internet and it was freaking fast as hell which made me happy as well.

So I played around installing some things and enjoying the non-wired glory of kubuntu. I had to restart my computer to get firefox to appear, so I restarted and after booting up again when I opened wireless assistant it was offline again and not finding my wireless card. I re-ran the command above and again it worked...

long story short, when I logged on this morning, I ran the command again but now it finds the access points but wont connect.

So 2 questions:

1. Is there a way to set my konsole to automatically run those commands when I log in?
2. Any Ideas as to why it is not connecting to the access points now?

---

### Post by ukulele_ninja on 2007-07-19
Well now after being plugged into ethernet... I ran the command again and re-opened my wrieless assistant and it said it connected to my access point...but it didnt move it to the top of the list and change the icon beside it and it wouldnt let me load the internet.

---

