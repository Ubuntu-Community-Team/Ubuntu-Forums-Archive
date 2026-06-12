---
title: "[SOLVED] ./configure not working"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by xyrer on 2007-02-13
Hi, i downloaded and application called stunnel and tried to install but when i type ./conf and hit tab it doesn't work, if write it ./configure it says permission denied, and with "sudo ./configure" it says command not found.

Anyone can shed a light on me about this?

---

### Post by taurus on 2007-02-13
What's the output of this command then, in the same directory where you tried to run the ./configure command?

```
ls -la
```

---

### Post by tbroderick on 2007-02-13
Make sure you have the build-essential package installed. Also, stunnel is in the repos. Either sudo apt-get install stunnel or stunnel4.

---

### Post by dexter on 2007-02-13
Is the configure script executable ? If not try 
chmod +x configure
and try running it again.

---

### Post by xyrer on 2007-02-13
thanks a lot for all the responses, the configure was in effect, not executable, i already had installed the build essentials, and ls -la showed indeed that configure is in the directory but no executable permissions, everyone of you gave me something to learn.

I finally installed from the repos, didn't know the "4" was missing, tried stunnel but got no response, finally stunnel4 did it more easily but i know what to look for next time i try to do ./configure.

Thank you everyone.

---

### Post by Bachstelze on 2007-02-13
If the configure script was not executable, all you need it to make it so :)

```
sudo chmod +x ./configure
```

---

