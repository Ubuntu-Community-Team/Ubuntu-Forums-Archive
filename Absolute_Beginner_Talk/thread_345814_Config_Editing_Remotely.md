---
title: "Config Editing Remotely"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Tspiritstorm on 2007-01-24
I made the switch to Ubuntu about two weeks ago after my first trial run with Redhat. My 10+ years of work experience is totally Microsoft based. My boss and I decided that we wanted to look for alternatives for our current OS solutions based of what we saw coming from Microsoft and the costs involved already. I decided on Ubuntu due to the great community I see. 

We are an ASP that also hosts DNS/EMAIL. We had a couple of Redhat Linux boxes inhouse when I came aboard 3 years ago and honestly they have been the most stable systems in our entire network. Anyway I wanted to see if I could redo our current mail server solution and started building the server a few days ago. I have enjoyed working on the OS and software more the last few days than in the last few years that I can remember. 

Sorry on to the question. I am trying to learn all the commands and since I have alot of knowledge in routers and security devices it hasn't been that hard to pick up. However I depend on remote access for everything. I need to be able to make changes from home without any issues. Most config files I open with gedit /etc/ and so forth but how can I do that remotely?

I may have more questions about some mail server issues soon but I am not finished trying to figure them out on my own, even at home which is why I am trying to figure out the right way to connect remotely. I can telnet and I can ssh but ssh doesn't allow me to open config files like it would from a terminal. Or am I wrong?

Thanks!

---

### Post by wimac on 2007-01-24
ssh in then use vim or nano to edit the files.

---

### Post by Tomosaur on 2007-01-24
Yup, ssh is all you need here. Just make sure to use a strong password :)

---

### Post by Tspiritstorm on 2007-01-24
Thanks! That is what I needed totally!

---

