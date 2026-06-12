---
title: "Download managers (axel and prozilla)"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by kitt on 2006-09-03
Hello everyone,
I use Ubuntu 6.06 on my acer aspire 5000 machine..and i have a small problem with using download accelerators.
I get a pathetic internet speed in my college dorm, and thats the only way i can access the internet. Theres a http proxy (and its quite restricitive )...
To speed up my downloads..i downloaded axel and prozilla. 
Unfortunately ( and i dont know why. ) none of them work. Both get stuck in the "initializing download" stage. However, the turbo-download-them-all extension in firefox works.

Can anyone tell me how i can solve my problem? I really need a download accelerator..because my friends using windows use the many download managers available for it and get a 10x speedup.. and i dont want Linux to lose in this battle against windows..

Thanks folks,

---

### Post by wangbin on 2006-09-03
I guess you didn't set the proxy correctly for your axel or prozilla?

---

### Post by Burke on 2006-09-03
Put this in your ~/.bashrc:

```

export http_proxy=[insert proxy location here]
export HTTP_PROXY=[insert proxy location here]
```

...then run "source ~/.bashrc" and see if axel works.

---

### Post by kitt on 2006-09-03
Thanks..
I exported my proxy settings to bashrc..but now i get "segmentation fault" as the error.. 
By the way..how exactly am i supposed to enter the proxy location? do i have to specify the port as well?

---

