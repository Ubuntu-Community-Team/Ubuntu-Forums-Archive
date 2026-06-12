---
title: "No Sound - help!"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by olivads on 2007-11-18
I am totally new to ubuntu. Old desktop crashed, friend let me borrow his old computer until I get a new one. His computer has Ubuntu - Feisty Fawn.

For some reason, I have no sound capabilities. It's on permanent mute (the volume icon in top right corner is muted, and it won't let me unmute).

I know the sound card works (it's so old it's part of the motherboard, not a separate card) because when Ubuntu loads, I hear drumbeats. But when I log in, all goes silent.

One thing might have caused this - my friend couldn't remember the username/password, so I went into the text-based screen and created my own username. Maybe this somehow caused sound issues.

Any step-by-step help would be greatly appreciated - thanks!

D.T.O.

---

### Post by Arthur Archnix on 2007-11-18
It's possible your user wasn't added to the sound group. Head over to users and groups, check out the properties on your user account and make sure you're a part of the sound group.

---

### Post by olivads on 2007-11-18
Tried to find "users and groups" on my system-administration menu - not there. Other ideas?

---

### Post by Pumalite on 2007-11-18
Post:
lshw -C sound

---

### Post by RockTonic3 on 2007-11-18
i don't suppose you can unmute the channel in alsamixer?

try running it as sudo <sudo alsamixer> and if the channel is muted push m while it's selected.

---

### Post by olivads on 2007-11-18
Got it to work - thanks!

I went into the root menu, and added my username as an admin. Then rebooted and "users and groups" was there. I added sound (and cd) capabilities and we are set!

Thanks for your help!

DTO

---

### Post by Arthur Archnix on 2007-11-19
That's great. It might help future users if marked your thread as solved. You can use thread tools to do so.

---

