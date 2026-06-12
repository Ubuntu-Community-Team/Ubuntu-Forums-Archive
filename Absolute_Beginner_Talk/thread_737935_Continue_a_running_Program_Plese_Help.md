---
title: "Continue a running Program?? Plese Help"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by sebkinne on 2008-03-28
Hello everyone,

I am running a game server, which runs 24/7. This i accomplished by using the programm screen before.
Basically it started it in screen -q "command", which then started the server in the screen and i could always access the server console. This always worked...UNTILL:

Yesterday i compiled some scripts for the server, and noticed that they are loaded at the startup of the server. HOWEVER, for some reason things do not work durning the couse of the game. Like pulling a lever which executes a script.

I thought it was out compile skills, and that we messed up, but later found out that when i start the programm in screen, the scripts dont work.

Now if anyone knows a way to make it work with screen, that would be brilliant. If any other ideas are present, shoot me.

Oh yea: When i just execute the program normally, without screen, of course it works properly. Then when i close the ssh terminal, the programm continues to run. If there is a way to grab that, sure, i could use that :)

Thank you so much and best regards,
seb

---

### Post by SpaceTeddy on 2008-03-28
how about you simply run "screen", which will the spawn a normal shell within screen. does the programm compile then (since now a shell is loaded within screen and the environment got set)?

if it does you can detach from the screen-session without it closing by holding ctrl down and pressing a and then d...

don't now if that makes a difference...

---

### Post by Oldsoldier2003 on 2008-03-28
nohup <yourprogram>
then close the terminal

---

### Post by sebkinne on 2008-03-28
well yea, and how do i reopen it?

seb

---

### Post by Oldsoldier2003 on 2008-03-28
> **sebkinne said:**
> well yea, and how do i reopen it?

seb

Unless you have a need to interact with the game server directly (or its compiled in such a manner that you must)  there is no need in running it via screen. Using nohup then killing the term you launched it with is a lot more resource smart.

---

### Post by sebkinne on 2008-03-29
Ok, thanks for all your help, but i i do actually need to interact with the server, because it has a server console.

i found out, that if i run "screen" command
then execute the script, that will work perfectly. However as soon as i use a command like

"screen /server-world"

it doesnt work anymore..

anyone help?

seb

---

