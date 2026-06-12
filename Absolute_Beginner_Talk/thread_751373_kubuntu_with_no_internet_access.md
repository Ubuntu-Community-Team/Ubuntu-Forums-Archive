---
title: "kubuntu with no internet access"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by JBSmo on 2008-04-10
I finally have permission to install a linux distro at work, in a restricted environment: the PC I will be able to install kubuntu on has no internet access. Not a problem for the initial install, I have the live CD. What I'm wondering about is how to go about getting additional packages or updates. Any suggestions?

Thanks!

---

### Post by Fate Reconciled on 2008-04-10
I suppose you could load debian packages on to a CD at home then install from the CD at work?

---

### Post by OffAxis on 2008-04-10
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by JBSmo on 2008-04-16
I appreciate your responses, but I guess I forgot to mention:

   I need to access the code via my windows box here at work.

   I'm still learning linux, and don't know where to look for the packages to download. The online documentation I've seen so far all seems to assume I will be accessing the repository via apt-get or aptitude or synaptic.

   Although I plan to install a dual-boot at home, this will be some time down the road since I need some additional hardware.

Any additional help is greatly appreciated.

---

### Post by JBSmo on 2008-04-16
AHA! I found it...

---

### Post by KMuchane on 2008-04-16
Hi! 


Navigate to the Synaptic Manager -System > Administration > Synaptic Manager. You will need to type in the password you used to login. 

Search for the package you want to Install.

Select to install it .
DO NOT click on apply.   
 Instead, Go to File and click on Generate Package download Script. 
This will prompt you on where to save the script. You can save on a flash stick. 
If you open the  file you  have just saved  in the stick  you will see that it contains URLs for the packages you selected for installation, including dependencies. 

Now go a computer connected to the Internet, paste the URLs and download the packages to a memory stick. 

Go back to your computer and install them. You are done!      

Hth ...

---

