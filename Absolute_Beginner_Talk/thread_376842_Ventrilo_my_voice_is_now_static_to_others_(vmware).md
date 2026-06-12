---
title: "Ventrilo my voice is now static to others (vmware)"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Scotty562 on 2007-03-05
Hello, just recently me and my friends started a ventrilo server. To connect I originally installed it on the windows xp vm I had setup and life was grand. I could hear everyone and everyone could hear me.

Today I attempted to run ventrilo through wine. It started and people could hear me but I coudln't use the press to talk button. So I downloaded a program that was suppose to solve that and it had me:

chown <your username> /dev/input/eventx
where x is number of right event device.

I don't know if that would have affected it or not but now when I chat through the vm all people here from me is static. I searched for alsa in synaptic and reinsatlled anything that has alsa in it but that didn't fix it.

I don't know what I changed or where to begin to look. What could have caused this and what can I check to fix it?

Edit: I found a + 20db button and that seems to have magically fixed everything. And a bonus people can hear me through vent run with wine!  Now I just can't run wine and have sound from any other source on my machine.  This is a small inconvenience but if anyone knows the solution that would be great!

---

### Post by Levenly on 2007-03-06
I've had the same problems too.  I fixed it by setting up alsa-oss, which runs OSS programs through ALSA.

sudo apt-get install alsa-oss

Then run the program through alsa-oss with

aoss wine /home/<user name>/.wine/drive_c/Program\ Files/Ventrilo/Ventrilo.exe

(or wherever you have your Ventrilo program located)

You can also run the other WINE programs through aoss wine, just make sure you enter in the correct path.

Hope that works.

---

### Post by Scotty562 on 2007-03-06
I followed your instructions and Ventrilo does start, however, I can't speak to others. It's almost like the mic isn't configured for alsa-oss.  I press my hotkey and my icon turns green as if I'm talking but no sound goes through.  Jump one hurdle and find another :(.

Thank you for the suggestion.

---

### Post by Scotty562 on 2007-03-24
Ok, now I can press the button for about 5 seconds and talk. After that when I press the "press to talk" button nothing happens. I can still hear others though.

---

