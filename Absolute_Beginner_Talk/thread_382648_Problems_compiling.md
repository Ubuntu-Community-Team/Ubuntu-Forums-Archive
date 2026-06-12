---
title: "Problems compiling"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by buffy^ on 2007-03-12
When trying to compile some source i am getting the error below.


[COLOR="red"]checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2                                                              .0 >= 2.12.0    atk >= 1.9.0    pango >= 1.12.0    cairo >= 1.2.0) were not met:

No package 'glib-2.0' found
No package 'atk' found
No package 'pango' found
No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/color]


I have downloaded glib etc and ran ./config and also a make on it but still is giving me the above error message, I am doing somthing wrong but cant work out what it is any ideas.

---

### Post by Bachstelze on 2007-03-12
```
sudo apt-get install libglib2.0-dev libatk1.0-dev libpango1.0-dev libcairo2-dev
```

Good luck :)

---

### Post by iCer' on 2007-03-12
thanks mate...

error now is:

[color=red]
Requested 'glib-2.0 >= 2.12.0' but version of GLib is 2.10.3
Requested 'cairo >= 1.2.0' but version of cairo is 1.0.4
[/color]
I tried to chnge version to download the one it asked for but no file found...

---

### Post by Bachstelze on 2007-03-12
Running Dapper ? The only thing you can do is upgrade to Edgy.

---

### Post by hod139 on 2007-03-12
What are you trying to compile from source?  It looks like it wants newer versions of the libraries than the ones in the repository.

---

### Post by iCer' on 2007-03-12
trying to compile airsnort.
ran ```

sudo apt-get dist-upgrade 
```

but the problem remains.

---

### Post by Bachstelze on 2007-03-12
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by iCer' on 2007-03-12
> **HymnToLife said:**
> [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)


have been on that link and tried to run the command it tells you...
```

gksu "update-manager -c" 

```

this appeared to update somthing, but then stopped...

have rebooted since, but unable to tell if it has actually updated to edgy - i suspect not (still same error when trying to compile)

---

### Post by hod139 on 2007-03-12
System->About Ubuntu 
will tell you what version you are running.  Alternatively, you can look at /etc/apt/sources.list and if you see dapper, you are running dapper.  If you see edgy, you are running edgy.  If you see a mix, something went wrong :)

---

