---
title: "It disappeared.."
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by arvacon on 2008-01-21
Hi,I changed the library object from wine's configuration and now wine doesn't open,even config window..From compiler if you type "wine confg" it is writing this:

wine: could not load L"c:\\windows\\system32\\confg.exe": Module not found
arvacon@arvacon-desktop:~$ err:module:import_dll Library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Library shell32.dll (which is needed by L"c:\\windows\\system32\\wineboot.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\wineboot.exe" failed, status c0000135

Have you any solution to suggest me friends?

---

### Post by skymera on 2008-01-21
what command did you use to get all that?

try reinstalling Wine

```
 sudo aptitude remove wine
sudo aptitude install wine 
```

---

### Post by MONODA on 2008-01-21
when u uninstall wine delete .wine in your home folder it should reset all of your settings and preferences for wine. it is what I do when I break and app

---

### Post by skymera on 2008-01-21
o yes, forgot to mention.
thanks.

---

### Post by arvacon on 2008-01-21
I uninstalled it but i cant find any folder from wine in the first page of home folder.Is it anywhere else?

---

### Post by MONODA on 2008-01-21
all files and folder starting with a . are hidden. Try viewing hidden folders(ctrl+h)

---

### Post by arvacon on 2008-01-21
oouaou!Finally every day is a new day! Thank you guys,for your right and quick response.

ps. After this code "sudo aptitude install wine" ,will wine take sudo force?Because this is not good,e?

---

### Post by arvacon on 2008-01-21
I am asking you about sudo because when a made install of wine,it did,t ask me password with the "sudo aptitude install wine".Why?

---

