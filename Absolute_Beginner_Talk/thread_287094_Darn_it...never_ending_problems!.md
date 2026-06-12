---
title: "Darn it...never ending problems!"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by hyby on 2006-10-28
Hi guys,

Decided to upgrade to Edgy today. Went well, i didnt get the error of a blank screen with 2 blocks anymore.

However, i still have my sound problem. Darn it! It just wont work!...I dont know what to do.


Anyway,  i thought i try to reinstall Beryl/Aiglx, but for some reason it wont work! I am following the guide. I have managed to get it to work in Dapper. I am up to the part where i have to download a new Xorg file "linux-dr-modules-2.6.17-generic. The site where i downloaded it from [http://hermies.net/download](http://hermies.net/download) is down. Does anyone know where i can download it from? 

I decided to proced with the installation with:
sudo ln -s etc, etc, into the xorg air folder but it doesnt exist. Do i need a different isntallation guide for edgy?

---

### Post by tronica on 2006-10-28
to use aiglx you need to use this command to run it, and you also need the nvidia beta drivers.

> beryl --force-aiglx --use-cow

run that along with beryl-manager at startup

---

### Post by hyby on 2006-10-28
Thanks,
but my bash doesnt recognise that i have installed beryl.

---

