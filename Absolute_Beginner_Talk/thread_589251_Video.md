---
title: "Video"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Brutus2006 on 2007-10-24
Ok 
I installed Gusty, had fiesty working like a top. I  went to Envy and downloaded the new video driver for my 128 Nvida Card. Now I get on my LG monitor Analog Out of range 68.8 khz/85hz and a black screen.

Please help Im lost here.

Any help will be appreciated

---

### Post by Bakon Jarser on 2007-10-24
I used envy when i first installed feisty but this time I did a clean install of gutsy and when it booted up it said something about restricted drivers in the corner so I clicked on it.  It asked for my password, I told it to use the restricted driver, and it worked just fine.  Had to use the terminal to access the nvidia control panel though and I don't remember the command, maybe someone else will post that for ya.

---

### Post by mikewhatever on 2007-10-24
The command for nvidia controls is 'nvidia-settings', but that would not work if there is no gui. It looks like your xserver needs to be reconfigured. Did you let envy do it? If not, you can boot into recovery mode, log in, start envy with 'sudo envy -t', and reconfigure x.

---

