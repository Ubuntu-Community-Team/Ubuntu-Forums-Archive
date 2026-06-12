---
title: "Compiling problems :("
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by beshroomed_hippie on 2007-04-12
Hello everybody! I just installed Ubuntu "edgy" yesterday on my powerbook G4, caving into my extreme curiosity about open source and linux. After the install finished , I giddily fired up the terminal, quickly banged out a simple test c++ hello world program so i could test the gcc compiler, and lo and behold there is a problem.
 I receive the following discouraging remark,
" gcc: error trying to exec 'cc1plus': execvp: No such file or directory "

 Now, I'm fairly sure gcc is installed properly, where do i get these files?
I've done some reading, but really can't seem to find the answer I'd be very thankful if anyone could please shed some light on this issue, I am sure i must just be doing something wrong..

---

### Post by Bachstelze on 2007-04-12
```
sudo apt-get install build-essential
```

---

### Post by beshroomed_hippie on 2007-04-12
Thank you very much!

---

