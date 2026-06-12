---
title: "Warcraft 3 Command !"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by ThRixXx on 2007-12-01
I have a folder on the Desktop named Stuff.
I use a acid loader and when I run it it tells me "Could not start War3.exe! Make sure the loader is in the same dir."

I read somewhere that u must use these commands.  Can u rite a command script that runs these commands ? How will one run them ?

pushd "path-to-war3.exe"
wine w3l.exe -opengl
popd

Thanks.

---

### Post by subs on 2007-12-01
write these commands in a file say "war3" then change permissions.... ie

> chmod +x war3

and then type out war3 in the terminal or Konsole when u wanna start warcraft....

if u want to run the file without being in the directory the file is stored in.... make the adjustment to the path variable for ur bash shell.... or just put a copy of this file in /bin

---

### Post by ThRixXx on 2007-12-01
Sorry u confuzed me, all I want to do is run w3l.exe with wine so that wine knows there is a war3.exe in the same directory !

---

### Post by subs on 2007-12-02
> **ThRixXx said:**
> Sorry u confuzed me, all I want to do is run w3l.exe with wine so that wine knows there is a war3.exe in the same directory !

no... u didnt understand me at all.....

the war3 i was referring to is a file called war3 which u create and not any of the files of which are installed in ur warcraft dir....

---

