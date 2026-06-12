---
title: "adding delay to a startup program"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by k9brand on 2006-10-08
I like Eterm.  I put it in the startup list (under "system > sessions").  However, I have it set for transparency and when it loads, the background hasn't completely loaded yet, so it looks all screwed up...


My question: In the startup section I have this code -
```
Eterm -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 79x40+760+319 -f white 
```

Is there any way to have it delayed by about 30 seconds to let everything load first?

---

### Post by jaboua on 2006-10-08
One possibility is to make an Eterm-launching script. Copy & paste this into a terminal:```
cat > launch-eterm << "EOF"
#!/bin/bash
sleep 30
Eterm -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 79x40+760+319 -f white
EOF
chmod +x launch-eterm
sudo mv launch-eterm /usr/local/bin
```

Then make the startup-script or what you had run /usr/local/bin/launch-eterm

---

### Post by Delkster on 2006-10-08
> **k9brand said:**
> My question: In the startup section I have this code -
```
Eterm -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 79x40+760+319 -f white 
```

Is there any way to have it delayed by about 30 seconds to let everything load first?

You could try this:
```
sleep <n>; Eterm -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 79x40+760+319 -f white 
```

Replace <n> with the number of seconds you want it to wait before proceeding.

---

### Post by slimdog360 on 2006-10-08
dont know how to do that but you could always look at konsole or my personal favourite yakuake. They both offer transparency.

---

### Post by k9brand on 2006-10-08
thanks for the replies!!

I tried:
```
sleep 15; Eterm -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 79x40+760+319 -f white 
```

and I also tried:
```
sleep <15>; Eterm -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 79x40+760+319 -f white 
```

but neither started the program at all. Am I missing something?

I am going to try everything else in this thread too.

---

### Post by k9brand on 2006-10-08
> **jaboua said:**
> One possibility is to make an Eterm-launching script. Copy & paste this into a terminal:```
cat > launch-eterm << "EOF"
#!/bin/bash
sleep 30
Eterm -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 79x40+760+319 -f white
EOF
chmod +x launch-eterm
sudo mv launch-eterm /usr/local/bin
```

Then make the startup-script or what you had run /usr/local/bin/launch-eterm


this worked for me.  thank you !

---

### Post by Delkster on 2006-10-10
> **k9brand said:**
> neither started the program at all. Am I missing something?

Probably not. In a terminal the semicolon can be used to separate two commands to be executed in sequence, so my example would have first executed "sleep 15", which would pause for 15 seconds and then return to execute whatever comes after that.

Since it didn't work, I guess Gnome doesn't allow multiple commands to be specified like that in the session settings. I thought it might work because it appeared that the Run Command dialog in Gnome (the one you get by pressing Alt+F2, if I remember the default keys correctly) would accept that syntax.

Another option instead of putting several commands on the same line like that is to put them in a script and then have that script executed on the session startup (or whenever you want the commands to be run), like in jaboua's working solution.

---

