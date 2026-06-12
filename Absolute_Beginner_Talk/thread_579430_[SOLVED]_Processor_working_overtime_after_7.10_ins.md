---
title: "[SOLVED] Processor working overtime after 7.10 install"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Morteno on 2007-10-18
I have just upgraded to 7.10 and I have noticed that my laptop is now considerably slower, the processor is constantly 90-100% in use and everything just takes longer. Does anybody else have the same problem and if so is there something I can do about it?

---

### Post by Beggar on 2007-10-18
What process is using your proc? open a terminal and type ```
top
```

---

### Post by NilsE on 2007-10-18
It is more than likely Tracker indexing your files for the first time.  

It will start up the indexing every boot and as time goes on it takes less and less after it gets the first full index.

---

### Post by Morteno on 2007-10-18
root is using about 60-65% of the memory, but there is only about 5 tasks running it says and 112 sleeping.

---

### Post by nikef on 2007-10-18
> **Morteno said:**
> I have just upgraded to 7.10 and I have noticed that my laptop is now considerably slower, the processor is constantly 90-100% in use and everything just takes longer. Does anybody else have the same problem and if so is there something I can do about it?


Sorry i cant help with your problem,but how long did it take for the upgrade ? , as i am doing mine now and it seems to be stuck  :confused:

---

### Post by Morteno on 2007-10-18
I downloaded it last night, about 2 hrs and the install took quite a bit longer so I left it overnight. I am downloading it to our other computer now and it seems to be taking around 5 hours because of the traffic. Have patience!

---

### Post by nikef on 2007-10-18
> **Morteno said:**
> I downloaded it last night, about 2 hrs and the install took quite a bit longer so I left it overnight. I am downloading it to our other computer now and it seems to be taking around 5 hours because of the traffic. Have patience!

Thank you ,i will let it run then

---

### Post by Morteno on 2007-10-18
> **NilsE said:**
> It is more than likely Tracker indexing your files for the first time.  

It will start up the indexing every boot and as time goes on it takes less and less after it gets the first full index.

Thanks Nils, I hope that is it. I'll check on it later and see if anything changed.

---

### Post by gabz8472 on 2007-10-18
I'm having the same problem and tried the "top" code given by one of the responses to this thread. I'm not a technical guy, so what am I looking for exactly?

---

### Post by Niniel on 2007-10-18
Why don't you just run the System monitor? (System/Administration/System Monitor) Go to the Processes tab and check out the % CPU column.

---

### Post by gabz8472 on 2007-10-18
I did that. Its running between 85-100% usage. This is strange because I just had this laptop repaired. Could this have some kind hardware problem as well?  Before the repair, it would rub between 15-40% and would only go up higher when I use graphics and media applications.

---

### Post by Niniel on 2007-10-18
Ok, looking at system monitor, which process exactly is using up all the cycles?

---

### Post by gabz8472 on 2007-10-18
Al the processes are reading "sleeping" except netstat which says "zombie".  in the terminal, using the "top" command, it shows that I have 112 process- 8 running, 104 sleeping and 1 zombie.

---

### Post by gabz8472 on 2007-10-18
This is really weird. I said that I had this laptop fixed. I tried to use a different battery pack and all of a sudden, the CPU usage is back to normal! Seems like that solved it! Thanks.

---

### Post by Niniel on 2007-10-18
Have you tried killing the process?

---

