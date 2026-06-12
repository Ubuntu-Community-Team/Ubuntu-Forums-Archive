---
title: "firestarter.sh missing"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by derekho55 on 2006-10-05
I have currently installed Firestarter 1.03 in my Dapper Drake Kubuntu. Installation went fine, and I think I installed all the dependancies correctly as well.

However, I tried to run firestarter via:
```
sudo firestarter -s
```

and a error message prints out:

```

Error spawning shell process: Failed to execute child process "firestarter.sh" (No such file or directory)
Failed to start the firewall
An unknown error occurred.

Please check your network device settings and make sure your
Internet connection is active.

```

I do have an active internet connection via cable. I have checked my "/etc/firestarter/" for firestarter.sh and it is not there.

How can I get this firestarter.sh?

Thanks in advance.

---

### Post by wieman01 on 2006-10-06
I think this more relating to the startup script in **/etc/init.d/** rather than /etc/firestarter/. Have you restarted the computer? 

If this does not help, I'll help write a boot script (later today... off for now).

---

