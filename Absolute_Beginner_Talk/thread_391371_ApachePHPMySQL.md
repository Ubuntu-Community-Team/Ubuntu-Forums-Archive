---
title: "Apache/PHP/MySQL"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by deuchar1 on 2007-03-23
Hey again guys,

Back again :)

I've installed apache2, mysql and php4 through Synaptic and I'm getting the apache welcome screen at 127.0.0.1 ok - one problem though - I don't have permissions to put files in the var/www folder. I figured I could copy them through terminal with the sudo command but is there any way of enabling access through the gui? Some kind of -r -w command or something I can run on the folder in terminal? 

Thanks,
G

---

### Post by Bachstelze on 2007-03-23
Some people might tell you to run nautilus as root so you can copy stuff to the folder. I personnally think it's a very bad idea and I'd rather recommend you chown the dir to yourself so you can put stuff in it without being root.

```
sudo chown -R $(whoami) /var/www
```

---

