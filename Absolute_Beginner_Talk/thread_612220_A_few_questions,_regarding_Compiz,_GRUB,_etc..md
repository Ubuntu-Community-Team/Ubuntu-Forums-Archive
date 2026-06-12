---
title: "A few questions, regarding Compiz, GRUB, etc."
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by SlalomMan on 2007-11-13
I'm kind of a beginning Ubuntu user--I installed Edgy for a bit and used it for a while, before getting a new laptop. I also ran Feisty for a bit, but ran into some hardware trouble with my new Toshiba. Finally, I decided to try Gutsy, and let me say, it has been working like a charm. All of my old hardware problems(speaker issues, wireless issues) are gone, but I have a few questions.

1)Does Ubuntu come with compiz/beryl already installed? I've looked in both the package manager and the add/remove programs and I couldn't find it.

2) Where are desktop effects? I wanted to enable them, but they aren't in my preferences menu like they used to.

3) Where is the Grub settings file where I can change the names/order of my boot systems?

4) For a programming class I am taking they are using Alice. It is available for Linux, but I can't seem to install it/run it. Any help here?

Thanks in advance.

---

### Post by zabien1970 on 2007-11-13
STOP Read top sticky first

---

### Post by shad0w_walker on 2007-11-13
First off. Don't run any command with rm in it. Its a spammer. Check the top sticky.

1.Compiz fusion is installed by default and should work out of the box when you install your graphics drivers.

2. They should be in your appearances menu. System > Preferences > Appearances > Visual effects

3. /boot/grub/menu.lst

4. Sorry, not a clue.

---

### Post by mysticrider92 on 2007-11-13
1) If you have ubuntu-desktop installed Compiz should be there.

2) See #1, maybe try sudo apt-get install desktop-effects.

3) The grub settings file is in /boot/grub/menu.lst.

4) Do you get any errors when running it? and what kind of file is it?

---

### Post by SlalomMan on 2007-11-13
IT's a java file--run-alice.java. I don't get any errors, it just pops up a terminal with a few status messages and then the terminal window closes and then nothing.

---

