---
title: "how to install something from a bin file???"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by FordInFlames on 2005-12-08
i have a bin file with  real player 10 gold i wanna install i have tryed double clicking it nothing happens! and i know i need to use the terminal but i dunno much commands! cuz i just switched from windows to ubuntu :D !
so pliz any1 help me!

PS: :(  i dont have internet on the computer i have ubuntu on! or else i wouldve used the sudo install command!

---

### Post by invalid on 2005-12-08
```
chmod +x file.bin
sh file.bin
```

You may need to do this as sudo, depending on where the file installs itself.

Cheers,
Cb

---

### Post by FordInFlames on 2005-12-08
sorry it didnt work! i tryed with sudo and without sudo ! maybe it's cuz i have it in a folder on my desktop i dont know!

---

### Post by Rochvellon on 2005-12-08
[QUOTE=FordInFlames]sorry it didnt work! i tryed with sudo and without sudo ! maybe it's cuz i have it in a folder on my desktop i dont know![/QUOTE]
In that case, put the file's whole address in the command, like
```
chmod +x /the/file/address/file.bin
sh /the/file/address/file.bin
```
You can see what is the address by copying it from Konqueror.

---

### Post by invalid on 2005-12-08
[QUOTE=FordInFlames]sorry it didnt work! i tryed with sudo and without sudo ! maybe it's cuz i have it in a folder on my desktop i dont know![/QUOTE]
You have to be a little more specific.

What did not work? Did you get an error? Can you copy paste it here?

---

### Post by tronica on 2005-12-08
First make sure you have excute permission, than type

./RealPlayer10GOLD.bin

---

### Post by FordInFlames on 2005-12-08
i wrote sudo something and the this appeared!

./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

but i shall try little more specific

---

### Post by tronica on 2005-12-08
libstdc++.so.5 needs to be installed, install it throught synaptic. But you will need an internet connection. Are you on broadband?
i got the ./RealPlayer10GOLD.bin install method of their website. It worked for me.

---

### Post by FordInFlames on 2005-12-08
libstdc++6_4.0.2-5 i got this one does that help :confused:
but where do i put it and use it

---

### Post by tronica on 2005-12-08
i think, install it and try install real again. It won't hurt

---

### Post by tronica on 2005-12-08
ok, i think i solved your prob. I tried this realplayer install on my other box, and had the same prob as you. OK, you need to install libstcdc++5-3.3-dev package and make sure you have gcc installed. If you try those and stilll nothing, then install all libstcdc++ dev's.

---

### Post by FordInFlames on 2005-12-08
encountered a new problem the usr file in the main drive i dont have permission to put anything there how do i do that??

---

### Post by tronica on 2005-12-08
On the main drve you would have to make new directory, but
you can try doing sudo ./RealPlayer10GOLD.bin or make a new folder in you home directory called real and then from the prompt 

type cd /home/yournamehere/real
then ./RealPlayer10GOLD.bin

---

### Post by FordInFlames on 2005-12-08
no i meant the libstdc++5-3.3-dev files and stuff

---

### Post by tronica on 2005-12-08
hmm, i know your getting tierd of this by now i'm sure but tell exactly what you did.

---

### Post by FordInFlames on 2005-12-08
i tryed moving some files by mouse into the usr folder in the main drive from the libstdc++5-3.3-dev_3.3.6-10_i386.deb in the data.tar to kind of install it or put it where i taught it belonged?

---

### Post by tronica on 2005-12-08
i'm noobie as well and i tried to chmod 744 /usr on mine and it messed it all up and i can't eve log into my machine.:???: so you can't install it through synaptic.

---

### Post by FordInFlames on 2005-12-08
oki but i need to go to bed my head hurts after all this stuff i have to do just to get a program installed!

---

### Post by tay on 2005-12-11
i'll keep on looking around..

root@sahaihost:/home/sahai/Desktop # sh /home/sahai/Desktop/amsn-0.94-3-linux-installer.bin
/home/sahai/Desktop/amsn-0.94-3-linux-installer.bin: /home/sahai/Desktop/amsn-0.94-3-linux-installer.bin: cannot execute binary file
root@sahaihost:/home/sahai/Desktop #

---

