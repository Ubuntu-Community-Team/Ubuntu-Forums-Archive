---
title: "Wine help?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by addysonclark on 2007-04-20
Hello my name is addysonclark. I literally just got ubuntu today. ( ditched the old windows and dove head first into the world of open source:)  ) So anyway the only games that I really play are WoW and Steam games ( CSS..and hopefully portal when it comes out :P ) and I heard these games work on ubuntu after reading some stuff online during school today. So I tried to follow some of the guides I found on the internet. They were all pretty simple to understand. Up until it got to the part involving wine. I can't seem to figure out how to run wine. Some places say to go to the terminal and type $ wine (nameofapplication).exe . but when i do that i get this....

"wine client error:1c: version mismatch 280/292.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running? "

On the winehq page it says to make sure i dont have any previous versions of wine. but i just downloaded ubuntu today so i didnt think that would be an issue.....please help?

---

### Post by bobplano on 2007-04-20
did you run sudo apt-get update before gertting wine? you probably need to uninstall wine then try reinstalling it. also use "wine --version" in the terminal and post what version you have here

---

### Post by addysonclark on 2007-04-20
i have wine-0.9.35


Now to try to uninstall i went to add/remove under applications and i cant find anything called wine in there.. 

(ps: thanks for such a fast response to my thread...(ubuntu : greatest community i've ever seen))

---

### Post by bobplano on 2007-04-20
just use the terminal to remove it. most of the support you get on these forums will be terminal commands so you need to get used to it anyway. sudo apt-get remove wine works just as well as add/remove or synaptic. well if you want to remove wine with add/remove you need to check "show unsupported applications"

---

### Post by addysonclark on 2007-04-20
Ok so the uninstall worked like a charm. Thanks! So now i can get wine threw the terminal? 

sudo apt-get wine?

---

### Post by addysonclark on 2007-04-20
Ok got it to sudo apt-get install wine... and that worked...but im still getting an error message when i try to run wine (winecfg or wine *.exe)

---

