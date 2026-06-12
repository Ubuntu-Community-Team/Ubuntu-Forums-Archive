---
title: "Having trouble with wine."
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by JohnnyQuickCash on 2007-07-03
Im trying to run DoD:S under wine but I cant figure out how to install it with wine. Any help would be great.

---

### Post by Rocket2DMn on 2007-07-03
I'm assuming you have wine setup and DoD:S means Day of Defeat: Source
Therefore, you need steam - you can download the steam installer from steampowered.com - it gives you an msi file which you can run lke so:
```
wine msiexec /i SteamInstall.msi
```
This will take you through the steam install.  You may need to run "winecfg" and set appropriate sound drivers (OSS or ALSA should work - people debate about which is better).
Once you have steam setup, you can download the correct games through steam using your own account.

---

### Post by JohnnyQuickCash on 2007-07-03
When I put that in it gives me an error saying "the specified istallation pakage could not be opened, Please check the file path. I have the file sitting on my desktop?

---

### Post by Rocket2DMn on 2007-07-03
you should probably move the file to wine's drive_c which will be here probably:
/home/yourusername/.wine/drive_c/
You can see that .wine folder in nautilus by hitting CTRL+H.
Then open a terminal and execute the command to install steam from there.  If THAT doesn't work, SteamInstall.msi MAY have to go into the /home/yourusername/.wine/drive_c/Windows/System32 folder, but that might not be necessary.

---

### Post by JohnnyQuickCash on 2007-07-03
Same message after I tried everything. Its sitting in the system32 folder

---

### Post by Rocket2DMn on 2007-07-03
Perhaps permissions need to be setup on the msi file.
```
chmod +x SteamInstall.msi
wine msiexec /i SteamInstall.msi
```
If this doesn't solve the problem, maybe wine needs to be reinstalled.
```
sudo apt-get autoremove wine
sudo apt-get install wine
```

---

### Post by JohnnyQuickCash on 2007-07-03
I just reinstalled it and it still gives the same error. Errrrr. Thats all I have to do to install wine right? Any settongs I need to change?

---

### Post by Rocket2DMn on 2007-07-03
OK, let's try the .exe file instead
download: [http://steampowered.com/download/SteamInstall.exe](http://steampowered.com/download/SteamInstall.exe)
then just
```
wine SteamInstall.exe
```

---

### Post by JohnnyQuickCash on 2007-07-03
Wow that worked like a charm. Didnt have to do anything. Thanks man.

---

### Post by JohnnyQuickCash on 2007-07-03
um well actually I cant see any words?

---

### Post by Rocket2DMn on 2007-07-03
Oh yeah, you need the Tahoma font.
"Steam requires the tahoma.ttf font. It is NOT included in the Microsoft core fonts package, so you have to get it separately.
For example, google for "filetype:ttf inurl:tahoma", download it and put it into your ~/.wine/drive_c/windows/fonts directory."
-from [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)
My bad!

---

