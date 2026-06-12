---
title: "I crashed my pacakge handler!?!?!?!?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by slacker3343 on 2007-09-09
Well I was attempting to install a program and it got hung up in the package handler so bad I had to kill to process. However, now when I try to install anything, even from the add and remove programs I cannot it keeps saying that it was interupted and I have to run the package handler manually to repair this problem in the command line......and it even geve me the instructions to do this. However I have no idea how to get out to the command line other than through the terminal so I can log in as root or superuser so I can fix the problem. If you can teach this old dog that trick it would be greatly appreciated. I feel like such an idiot even for asking but I can some but that I have not figured out and I feel really stupid so if you can help me I would greatly appreciate it

---

### Post by overdrank on 2007-09-09
> **slacker3343 said:**
> Well I was attempting to install a program and it got hung up in the package handler so bad I had to kill to process. However, now when I try to install anything, even from the add and remove programs I cannot it keeps saying that it was interupted and I have to run the package handler manually to repair this problem in the command line......and it even geve me the instructions to do this. However I have no idea how to get out to the command line other than through the terminal so I can log in as root or superuser so I can fix the problem. If you can teach this old dog that trick it would be greatly appreciated. I feel like such an idiot even for asking but I can some but that I have not figured out and I feel really stupid so if you can help me I would greatly appreciate it


HI in the terminal you can use the command given I think it would be something like
```
sudo dpkg --configure -a 
sudo apt-get install -f
```

---

