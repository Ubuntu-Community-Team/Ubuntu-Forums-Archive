---
title: "sudo nvidia-xconfig
sudo: nvidia-xconfig: command not found ???"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by medya on 2006-06-05
I am trying to install my nvidia driver from supported wiki
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)

but when I enter sudo: nvidia-xconfig
it says : command not found


I have installed nvidia-glx-legacy

---

### Post by %hMa@?b&lt;C on 2006-06-05
post the exact terminal output and input.  if you used the colon after sudo, try it with out the colon

---

### Post by medya on 2006-06-05
> fred@fred-desktop:~$ sudo nvidia-xconfig
Password:
sudo: nvidia-xconfig: command not found
fred@fred-desktop:~$


still the same

---

### Post by terminatorkobold on 2006-06-07
You can look in synaptic if you have the nvidia-xconfig package installed.

However if you are using dapper drake and the nvidia-glx driver you don't need nvidia-xconfig. You can configure your driver after having installed it with the application found under applications>system tools

---

### Post by tseliot on 2006-06-07
Explanation:
nvidia-glx includes also nvidia-xconfig
if you install nvidia-glx-legacy you have to install nvidia-xconfig separately.

Type:
sudo apt-get install nvidia-xconfig

---

### Post by cogadh on 2006-06-07
I'm currently running on Breezy and I installed nvidia-glx and nvidia-settings packages. I have looked through both packages and "nvidia-xconfig" is not an installed file in any of them. The nvidia-xconfig package also does not appear to be a part of any of the default repositories, is it in one of the Universe/Multiverse repositories?

---

