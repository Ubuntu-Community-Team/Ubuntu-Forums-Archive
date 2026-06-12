---
title: "Installing vent with wine?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by kingvicious on 2006-08-06
well ok i got wine installed and everthing on my computer i know how to open it. But what i dont understand is how do i install a windows program on with wine? like right now i have ventrilo i downloaded it on my computer but i dont know how to install it through wine. so anywas can someone help me?

---

### Post by kingvicious on 2006-08-06
*bump

---

### Post by Svenstaro on 2006-08-06
I think I've got just the thing: [http://slinux.net/how-to-install-ventrilo-2-3-on-linux](http://slinux.net/how-to-install-ventrilo-2-3-on-linux) 
:)

---

### Post by kingvicious on 2006-08-06
well this is for cedega. are installing programs and games on cedega and wine the same?

---

### Post by Svenstaro on 2006-08-06
Well, basically the only thing you have to do from that tut is getting the codec. All other stuff with wine. wine ventsetup.exe - Install - get codec + register it - wine ventrilo.exe 
Bam! You're done. No cedega needed at all. You may need the oss-alsa plugin though.

---

### Post by kingvicious on 2006-08-06
iam sorry but iam totally noob excepically about wine i've never used it and well i just installed it so mmm inno what the codec are lol are u talking about step 4? thats what i gotta do? how do u start wine 2? is winecfg it? cuz i go into that but it looks to me to be just a properties thing not the acuatl wine program. but anywas i realized that i had to go into the desktop/c/program/ and then create a vent folder but well after that iam lost :P

---

### Post by Svenstaro on 2006-08-06
Okay right, sorry. Have you installed vent yet? If not, type wine ventsetup.exe (or whatever it's called) to install it. Also make sure you use a recent wine version by updating your repositories (sudo apt-get update && sudo apt-get install wine) Google for the codec that you need and dl it. Follow the instructions in the tut for that part. Then navigate to the dir which you've installe vent to. That's most likely in your home-dir but hidden. (directories/files with a "."/"dot" in front of it are hidde so in case you are using nautilus (the gnome file browser) you'd need to enable hidden files first. From your home browse to .wine/c_drive/programs/vent or wherver you've installed it to and type wine ventrilo.exe. You can also try doubleclicking if it is properly installed. For reference you might find this interesting: [http://www.ubuntuforums.org/showthread.php?t=41737](http://www.ubuntuforums.org/showthread.php?t=41737)

---

### Post by kingvicious on 2006-08-06
well wait
i downloaded vent off the site but its not installed but uh where do i put the file so that i can do wine ventsetup.exe ?

---

### Post by Svenstaro on 2006-08-06
Your home dir will do just fine. That's the one called after your user.

---

### Post by kingvicious on 2006-08-06
exactly how do i get the MSI files tho the download page doesnt make much sense to me

---

### Post by kingvicious on 2006-08-07
ok i tryed the secound link you gave mes tutorial and at the end i get this error kingvicious@kingvicious:~/ventrilo$ wine ./ventrilo-2.3.0-Windows-i386.exe
err:module:import_dll Library msi.dll (which is needed by L"c:\\windows\\system32\\msiexec.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\msiexec.exe" failed, status c0000135
kingvicious@kingvicious:~/ventrilo$
 any ideas?

---

### Post by Svenstaro on 2006-08-07
Okay sorry, seems like you need those MSI files, though I didnt. On [http://slinux.net/how-to-install-ventrilo-2-3-on-linux](http://slinux.net/how-to-install-ventrilo-2-3-on-linux) get the MSI files like in the first step. Put em to your dir and install them. THEN try installing ventrilo. I'm gonna go sleep now, wish you the best of luck. I'm gonna be back in 7 hours or so.

---

### Post by kingvicious on 2006-08-07
well Svenstaro hopefully u read this when u wake up because i dont under how to get these msi files i really dont understand the links way of describing this at all X'(

---

### Post by Svenstaro on 2006-08-07
Good morning :)
Go here: [http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=CEBBACD8-C094-4255-B702-DE3BB768148F](http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=CEBBACD8-C094-4255-B702-DE3BB768148F)
Click on Download files below in the blue bar and download InstMsiA.exe in the lower part of the page. Put this into your home dir and type (in a terminal) wine InstMsiA.exe. Install it and try to install ventrilo afterwards.

---

### Post by kingvicious on 2006-08-07
hey good mouring to you too :P iam glad you found this well iam try to install them files i already had em downloaded i just didnt know what the hell to do with with em :P

---

### Post by kingvicious on 2006-08-07
ok i put wine in my home directory or atleast what i think is my home directory :P thats the folder that has the name on it that i gave to my computer or mybe username inno there both the same name on my computer lol
but anyways after trying wine instmisa.exe or what ever i get this error

kingvicious@kingvicious:~$ wine instmsia.exe
fixme:msiexec:main /regserver not implemented yet, ignoring
fixme:msiexec:main /unregserver not implemented yet, ignoring

---

