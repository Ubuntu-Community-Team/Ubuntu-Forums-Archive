---
title: "how do u install a python app?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2007-03-31
i downloaded a python app to read my motherboard sensors.In the folder there is a files called setup.py how do i run this to install the app?

---

### Post by picpak on 2007-03-31
What's the name of the program? If it's in the repositories, it'll be easier to install.

---

### Post by fdrake on 2007-03-31
if you have python installed you just need to run that script from the command line "./setup.py" and it will guide you through the installation. but you need to make sure you have python installed on your sys.

---

### Post by lime4x4 on 2007-04-01
the name of the app is called pyuguru and it's not in any of the repos

john@john-desktop:~$ sudo apt-get install python
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
john@john-desktop:~$ cd Desktop/pyuguru-0.1
john@john-desktop:~/Desktop/pyuguru-0.1$ ./setup.py
bash: ./setup.py: Permission denied
john@john-desktop:~/Desktop/pyuguru-0.1$ sudo ./setup.py
sudo: ./setup.py: command not found
john@john-desktop:~/Desktop/pyuguru-0.1$

---

### Post by 3rdalbum on 2007-04-01
Try this:

```

sudo su
python setup.py

```

The reason why you're getting "permission denied" errors is because you have not made the Python script executable. Right-click it, go to Properties and then to the Permissions tab. There you can set the "executable" permission for the file.

---

### Post by fdrake on 2007-04-01
same thing like 3rdalbum said but you can use the terminal to do this
sudo chmod 755 setup.py

---

