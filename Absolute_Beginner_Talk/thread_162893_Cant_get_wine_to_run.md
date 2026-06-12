---
title: "Cant get wine to run"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by Muag on 2006-04-19
Ok, i downloaded and installed wine now i cant get it to run...i dont know exactly how to...i downloaded wormux and got that to work just fine...any help?

---

### Post by Mustard on 2006-04-19
Can you be more specific about how you are trying to run it?

Normally its done via the command line like this...

```
wine /path_to_windows_application/name_of_windows_application.exe
```

Wine installs applications in a hidden folder in your $HOME directory called .wine.  To see it you would need to enable 'Show Hidden Files/Folders' in your Nautilus settings, or you could view it in command line..
```
cd ~/.wine
#change working directory to .wine

ls -al
#lists all files/folders in current directory
#including hidden files/folders in long format
```

---

