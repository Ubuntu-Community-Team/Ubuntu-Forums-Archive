---
title: "Need assistance with an installed package (libmail-perl)"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by Susan.Desanco on 2006-07-05
Hola, everybody...

I'm an excited new user to Ubuntu.  I've learned how to dual boot with Windows XP (major success for small me!), and I turned on the multiverse/universal repositories in the installer.  I used Synaptic to search for a program that I can utilize to send emails to members of my community, and it returned with:
   ***libmail - bulkmail - perl***

This seemed to be a good fit from its file description, so I downloaded it.  Now, I noticed that later, when I searched to find this libmail, it had went automatically to this directory:
   ***/usr/lib/mozilla-thunderbird/components***

In that directory, there are actually two files:  ***libmail.so*** , and, ***libmailcomps.so***

But when I go now to Thunderbird (which I had previously downloaded, and which seemed to automatically install) I don't find any options for making use of this libmail.  How do I 'turn it on' now that I have downloaded it?

---

### Post by ape on 2006-07-05
Susan,

  The libmail-bulkmail-perl package you installed has nothing to do with the two libmail* shared libaries installed for Thunderbird.

  The libmail-bulkmail-perl package installs the Mail::Bulkmail perl module that you can use to write your own bulkmailer in 

  What exactly are you trying to do that can't already be done in Thunderbird (or any other available mail client)?

--Ape--

---

### Post by Susan.Desanco on 2006-07-05
Hola ape!

I am new user to Linux, and I am using **Thunderbird version 1.5.0.4**
on the **Ubuntu 6.06** desktop distribution .

I have some  questions -- I am grateful for any help --
regarding a specific task I am trying to accomplish with Thunderbird...

First, here are those questions:
**(a)**  Does Thunderbird have the **functionality** to do the task below?
**(b)**  What additional program or package would I need to go along
     with Th'bird to **tie the variable data to the email** creation?

**(c)**  Any limitations/restrictions **I should be thinking about** regarding the task described below?

Here is the **TASK**:
I would like to use Thunderbird (Linux/GNU) to send out a few hundred emails to members of my service organization,
for which I finally made a web site. The email would go as follows: :**variable fields in these dots**:

--------------------------------------------------------------
To: :**variable** email address:
Subj: For :**variable** Tom: from Susan.DeSanco of AZ-United Way

When we were in contact last :**variable** December: we discussed the idea of :**variable** service task:. I'm happy to announce that we now have a web site with forums where our members can discuss this idea as a public group... etc.
----------------------------------------------------------------

Thanks in advance to you!!!

---

### Post by ape on 2006-07-05
Susan,


  Let me do some digging around and see what I can find.  Using a perl script and the Mail::Bulkmailer module, I'm sure something could be written to do what you want.  I'll check and see if I can locate any existing solutions.

--Ape--

---

### Post by Susan.Desanco on 2006-07-05
[quote=ape]Susan,
 
 
Let me do some digging around and see what I can find. Using a perl script and the Mail::Bulkmailer module, I'm sure something could be written to do what you want. I'll check and see if I can locate any existing solutions.
 
--Ape--[/quote]
 
Wow, Ape, that is very generous of you !!  I am usually quite adept at Googling for any info, but this particular task (perl script writing) would require a step beyond merely searching.  Thank you so much for taking up my request!

---

