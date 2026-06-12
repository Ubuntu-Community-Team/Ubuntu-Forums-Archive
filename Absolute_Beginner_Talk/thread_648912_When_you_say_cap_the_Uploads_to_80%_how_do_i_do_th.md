---
title: "When you say cap the Uploads to 80% how do i do that?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2007-12-24
Hi,

I use aMule and people keep saying cap the uploads to 80%...

my question how do you get the figure? 80% of what? is there a way to caculate it?...

Thanks..

---

### Post by hopelessone on 2007-12-24
i went to test my connections at a web site this is what i got:

:::.. testmy.net test results ..:::
Download Connection is:: 3003 Kbps about 3 Mbps (tested with 2992 kB)
Download Speed is:: 367 kB/s
Upload Connection is:: 10789 Kbps about 10.8 Mbps (tested with 5983 kB)
Upload Speed is:: 1317 kB/s
Tested From:: [http://testmy.net](http://testmy.net) (Main)
Test Time:: 2007/12/24 - 6:01am 
D-Validation Link:: [http://testmy.net/stats/id-04E2FUC7D](http://testmy.net/stats/id-04E2FUC7D)
U-Validation Link:: [http://testmy.net/stats/id-8K7T5ZG1S](http://testmy.net/stats/id-8K7T5ZG1S) 
User Agent:: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11 [!]

so cap the Upload to 8Mbps ???

Or just leave it all alone??

---

### Post by kpkeerthi on 2007-12-24
Sounds to me it is **80% of your upload speed limit** (not the upload bandwidth). So it is 80% of 1317 Kbps = **?**

---

### Post by hopelessone on 2007-12-24
Ahhh...thanks...

1053KB/s is right?

---

### Post by hopelessone on 2007-12-24
in the how to:
Slot allocation means how fast aMule should upload to each client. I recommend dividing the upload bandwidth by a factor of 5-6, so that an upload of 100 kB/s gives some 16-20kB/s per client.

so same deal?

1317 Kbps / 5 = 263 ??? <- is this right??

thanks..

---

### Post by daengbo on 2007-12-24
Why is your upload speed four times your download spped? That sounds wrong.

---

### Post by hopelessone on 2007-12-24
dunno the internet provider in South korea i suppose...

---

### Post by hopelessone on 2007-12-24
the slot allocation takes a maximum of 100KB/s...what should i set this to?

Back to 2KB/s..??

thanks...

---

### Post by Hallvor on 2007-12-25
In most cases ISPs offer the speed in kiloBITS, and not kiloBYTES. I think you will have to divide your numbers by a factor of 8.

Your maximum upload should then be 164,6 kB/s. 

Multiply by some 0,8 to get 80% of that value will give 131,7 kB/s.

Divide by 6 to get slot allocation, and you will have some 21,8... Just make that 22.

Anyway, you can experiment a little with these values. All that matters is that the upload speed doesn`t choke your regular internet traffic and your incoming downloads. As for slot allocation, all that matters is that you have a reasonably stable upload speed to use resources as well as possible.

In other words, try setting the upload speed to 130 or something like that, and slot allocation to a little more than 20 and see how it works.

---

