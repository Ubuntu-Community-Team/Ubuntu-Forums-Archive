---
title: "Four presumably easy questions"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by kevind23 on 2007-10-22
Hey! :) I'm not necessarily new to *nix, but this is my first time running any distribution as my main operating system! So, I just have four simple questions..if you can help please do :) Thank you

1. Keyboard Special Buttons -- They worked with GNOME settings, but then I was prompted and I chose the X settings and they stopped working. =(

2. Audio Output -- I have a Logitech 6-channel speaker system, but Ubuntu (I have played with the settings for a while) absolutely REFUSES to play audio on all but two channels. =(

3. Widgets -- How do they work? I've seen them before and I don't know how to use them/install them..etc. I would like to know more about this.

4. Finally, the dock bar. I have seen *countless* screenshots of various distributions of Linux and most seem to have a Mac-esque dock bar on the bottom. How do I achieve this on x64?

---

### Post by PurposeOfReason on 2007-10-22
1. I would assume you chose a different keyboard layout than before. Change it back.
2. I only have two speakers so I don't know.
3. gDesklets is probably your best bet. It's in the repositories. Install and run with gdesklets. It'll bring up a GUI to add widgets and you can get more from their site.
4. You're probably seeing AWN (avant-window-navigator). There is a howto for it.

---

### Post by adamorjames on 2007-10-22
> **kevind23 said:**
> Hey! :) I'm not necessarily new to *nix, but this is my first time running any distribution as my main operating system! So, I just have four simple questions..if you can help please do :) Thank you

1. Keyboard Special Buttons -- They worked with GNOME settings, but then I was prompted and I chose the X settings and they stopped working. =(

2. Audio Output -- I have a Logitech 6-channel speaker system, but Ubuntu (I have played with the settings for a while) absolutely REFUSES to play audio on all but two channels. =(

3. Widgets -- How do they work? I've seen them before and I don't know how to use them/install them..etc. I would like to know more about this.

4. Finally, the dock bar. I have seen *countless* screenshots of various distributions of Linux and most seem to have a Mac-esque dock bar on the bottom. How do I achieve this on x64?

Well, I can't help much but I can tell you that the dock bar is called AWN which stands for Avant Window Navigator. There is a theme for it I think at [http://sourceforge.net/projects/mac4lin](http://sourceforge.net/projects/mac4lin).

---

### Post by kevind23 on 2007-10-22
> **PurposeOfReason said:**
> 1. I would assume you chose a different keyboard layout than before. Change it back.
2. I only have two speakers so I don't know.
3. gDesklets is probably your best bet. It's in the repositories. Install and run with gdesklets. It'll bring up a GUI to add widgets and you can get more from their site.
4. You're probably seeing AWN (avant-window-navigator). There is a howto for it.

1. How? I never changed the keyboard layout, it just prompted me whether to use X's settings or GNOME's, and I chose X
3. Thanks :D
4. Actually, I think I was seeing Kiba-Dock but that doesn't run on x64, I'll look into AWN, thank you

---

### Post by PurposeOfReason on 2007-10-22
> **kevind23 said:**
> 1. How? I never changed the keyboard layout, it just prompted me whether to use X's settings or GNOME's, and I chose X
3. Thanks :D
4. Actually, I think I was seeing Kiba-Dock but that doesn't run on x64, I'll look into AWN, thank you
I've used AWN, IMO it's far easier to change and is moving much quicker at the moment. For the keyboard you change the layout (I think, I'm using fluxbox and this is from memory), system,  > preferences > keyboard layout. Worst case scenario you have to use xbindkeys which I have no knowledge of.

---

### Post by kevind23 on 2007-10-23
Okay, AWN works like a charm ^^, but the keyboard issue..I rebooted and it asked me again which settings to use; this time I chose GNOME, but now whenever I use a button it opens up a new instance of whichever application is assigned to the button, but without a titlebar.

Still need some help with the speaker settings, and *gDesklets doesn't seem to be working* -- **Update:** I had to compile it myself, but it works just fine now. (As a side note, <strike /> would be nice :P)

---

