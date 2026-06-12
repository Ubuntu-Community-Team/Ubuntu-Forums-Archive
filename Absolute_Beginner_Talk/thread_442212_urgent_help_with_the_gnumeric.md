---
title: "urgent help with the gnumeric"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by ajeetraj on 2007-05-13
Hello everyone, 
I am a third year physics student and i am doing my research and I am in a big trouble as i can't figure out how to make a proper histogram. I am using gnumeric and i don't really know how to create the bins for the histogram. I also tried the matlab but the same problem with the bins. 

I have around 50,000 data points in a column and I have to make a histogram of the data points against their frequency...in other words just the plot of the data points against their counts. 

I am attaching the file below which i have to create the histogram for...if anyone out there can help me with this then i will be so thankful to you. I have to submit the paper in one day and its really really urgent and ubuntu forum is one of my last option for help. please someone help me!!!!
thank you so much in advance and I will be waiting for your reply...

---

### Post by seatopia on 2007-05-15
In matlab use the command hist to create a histogram (try help hist).

N=hist(DATA,X)  will return the frequency (N) of DATA in bins centered at X.  You can plot it in matlab, or export the data to another program for plotting.

---

### Post by ajeetraj on 2008-02-22
Thanks! It did help and sorry I just forgot to thank you!

---

