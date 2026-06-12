---
title: "external speakers make no sound..."
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by i_a_coops on 2007-03-19
i have ubuntu on a mac, and the internal speaker works fine but there's nothing coming out the speaker output on the back.... which is a shame coz the internal speaker is pretty bad for music. i know the speakers work, they work fine in mac os x. i have to be missing something pretty fundamental here lol! oh yeah, and are there any alternatives to rhythmbox? just wondering...

---

### Post by DougieFresh4U on 2007-03-19
There's Exaile, Listen, amarok, also streamtuner (have a look through Add/Remove) which has hundreds of commercial free stations. As for your sound output not sure what to tell you. Maybe open alsamixer from terminal. Just open terminal and type **alsamixer** see that nothing is muted and maybe right click volume control in upper right corner and open volume controls and check whats ticked off in there.

---

### Post by gilgongo on 2007-03-19
I don't know if this is your problem, but what worked for me is this:

1. Open a terminal
2. Type "alsamixer"
3. You will see an application that looks like it came out of the 1980s.
4. Use the arrow keys to navigate to the output volume you want and turn it up, or unmute it (using the "m" key) if necessary. You may have to mute/unmute/modify other things too.
5. Hit Esc to save and see if you now have better sound.

---

