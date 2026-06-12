---
title: "nvidia drivers"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2007-04-13
i get this error when i used this command for install nvidia drivers.
sudo apt-get install nvidia-glx
```

Do you want to continue [Y/n]? y
Err http://archive.ubuntu.com feisty/main linux-image-2.6.20-14-386 2.6.20-14.23
  403 Forbidden [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-386_2.6.20-14.23_i386.deb  403 Forbidden [IP: 91.189.89.8 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```

---

### Post by Bachstelze on 2007-04-13
For some reason, access to this file on the repos is forbidden. Anyway, you should use the generic kernel instead of the 386 :

```
sudo apt-get install linux-generic
sudo apt-get install nvidia-glx
```

---

### Post by jasonpeinko on 2007-04-13
still same error

---

### Post by Bachstelze on 2007-04-13
Exactly the same or with a different filename ?

---

### Post by jasonpeinko on 2007-04-13
```
Do you want to continue [Y/n]? y
Err http://archive.ubuntu.com feisty/main linux-image-2.6.20-14-386 2.6.20-14.23
  403 Forbidden [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-386_2.6.20-14.23_i386.deb  403 Forbidden [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by Bachstelze on 2007-04-13
When you're running *sudo apt-get install linux-generic* ?

---

### Post by jasonpeinko on 2007-04-13
no that runs fine, but the nvidia part run gives that error

---

### Post by Bachstelze on 2007-04-13
Then you first need to reboot, choose the newly installed generic kernel and then remove the old 386 one.

---

### Post by jasonpeinko on 2007-04-13
still same error.

---

### Post by Bachstelze on 2007-04-13
```
sudo apt-get install linux-restricted-modules-2.6.20-14-generic
```

What does that give you ?

---

### Post by jasonpeinko on 2007-04-13
that installs fine

---

### Post by jasonpeinko on 2007-04-13
is it because feisty is not supported yet?

---

### Post by jasonpeinko on 2007-04-13
why i try to enable the restricted driver i get this error:
```

E: /var/cache/apt/archives/nvidia-glx-legacy_1.0.7184+2.6.20.5-15.20_i386.deb: subprocess pre-installation script returned error exit status 2
```

---

### Post by jasonpeinko on 2007-04-13
please help

---

