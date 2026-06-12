---
title: "Mplayer menu issue"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by anhtran81 on 2006-01-03
Hi all,

just a simple problem with MPlayer. It does not stop it functioning but rather annoying. When i tried to run mplayer, it does not show the control menu. It only display the large window, and i have to right click on it to open movie.

I tried to install with apt-get and compile from cvs but still have the same problem. Could anyone please shed me some light as I obviously missing something simple.

Thanks in advance.

Anh

---

### Post by mcduck on 2006-01-03
I think the package that includes the menu is called gmplayer or something.. try 'apt-cache search mplayer' or search in Synaptic to find what you need.

edit: gmplayer is not a different package, but is included with mplayer. So to get the control menu use command 'gmplayer' instead of 'mplayer'

---

### Post by anhtran81 on 2006-01-03
Thanks for a quick response.

I should be a bit clear on the issue. I am infact using gmplayer. I can see the gui interface. Down on the task bar, it had 2 tab name mplayer, one belongs to large window and the other is small control window. But for some reason it does not display so the only way for me to open a file is by right-click on the main window, pop-up window appears and open the file from there.

I tried Kubuntu unofficial guide on other machine and it works perfectly but that source is for Hoary so I am wonder why it does not work with breezy. Any idea?

Thanks

---

