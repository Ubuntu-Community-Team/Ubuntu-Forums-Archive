---
title: "Getting CastPodder to run?"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by harperd on 2006-05-30
I have just 'installed' CastPodder but it does not appear on any menu. How do I run it? I've looked through the documentation and tried numerous things but to no avail.  

Getting this fixed is my last step before moving over from Windows XP sop would appreciate any pointers.

Thanks
David Harper
Madrid Spain

---

### Post by richbarna on 2006-05-30
1. You can try pressing Alt+F2 to get the run dialogue box and then type castpodder.
2. On KDE there is a program called kappfinder that searches for non kde installed programs and puts them on the menu .-
In the terminal/console type :-
> sudo apt-get install kappfinder
3. Have you tried ipodder, or penguin tv ? They are available for download in the repositories too.

---

### Post by harperd on 2006-05-30
Thanks. Neither ipodder or Penguin TV appear in Synaptic Package Manager when I do a search. Kapfinder was already installed.

---

### Post by richbarna on 2006-05-30
I saw them in the repositories.
Maybe you should update your souces.list.
> sudo apt-get update
> sudo apt-get upgrade

---

### Post by harperd on 2006-05-31
Thanks for your help. Still can't see them! I seem to be missing something. I'm thinking of putting up a new thread asking for info about the best podcast client that's easy to install. I thought it would be :-k

---

### Post by richbarna on 2006-05-31
I'm running Dapper, maybe they aren't in the Breezy repositories.

---

### Post by harperd on 2006-05-31
I'm on Dapper too! Anyway, I've managed to get Gpodder working although I'm not sure how. It's very clunky compared to Doppler which I've been using in Windows so I'll test it out over the next day or two.

As a newbie, I'm getting a little frustrated by the difficulty in getting apps installed. I also found that after upgrading to Dapper, Windows was wiped from the Grub Menu.lst file so I could'nt boot into Windows and had to manually edit the file.

Despite the difficulties, I sticking with it  - having more fun than pain (just)

---

