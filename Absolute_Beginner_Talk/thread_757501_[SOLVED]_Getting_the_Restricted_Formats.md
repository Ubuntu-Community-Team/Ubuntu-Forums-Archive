---
title: "[SOLVED] Getting the Restricted Formats"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by AeThEr777 on 2008-04-17
So I tyoed in the following cmd in the terminal to get the restricted formats:

"sudo apt-get install ubuntu-restricted-extras"

Then it went through the downloading process everything looked fine untill i was prompted with the following screen which i cannot get past:

" Configuring sun-java6-bin  
        its subject matter.  It supersedes all prior or contemporaneous       &#8593;  
 &#9474;     oral or written communications, proposals, representations and        &#9618;  
 &#9474;     warranties and prevails over any conflicting or additional terms      &#9618;  
 &#9474;     of any quote, order, acknowledgment, or other communication           &#9618;  
 &#9474;     between the parties relating to its subject matter during the term    &#9618;  
 &#9474;     of this Agreement.  No modification of this Agreement will be         &#9618;  
 &#9474;     binding, unless in writing and signed by an authorized                &#9618;  
 &#9474;     representative of each party.                                         &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; For inquiries please contact: Sun Microsystems, Inc., 4150 Network        &#9618;  
 &#9474; Circle, Santa Clara, California 95054, U.S.A.                             &#9618;  
 &#9474;                                                                           &#9646;  
 &#9474; DLJ v1.1                                                  27APR2006ANS    &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>  

Any ideas on how to get past this point?

---

### Post by SunnyRabbiera on 2008-04-17
eh, if you want you can add the medibuntu repo:
[here]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by joshrobinson on 2008-04-17
what happens if you use synaptic to install it?

---

### Post by AeThEr777 on 2008-04-17
I already have added those. Now when i try to use either the add/remove or the terminal i get the following msg:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

Whats the problem now?

---

### Post by aysiu on 2008-04-17
> **AeThEr777 said:**
> I already have added those. Now when i try to use either the add/remove or the terminal i get the following msg:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

Whats the problem now?
Paste in ```
sudo dpkg --configure -a
```

---

### Post by AeThEr777 on 2008-04-17
Ok heres the output from that code:

"Setting up java-common (0.26ubuntu1) ...

Setting up odbcinst1debian1 (2.2.11-16) ...

Setting up unixodbc (2.2.11-16) ...

Setting up gcc-3.3-base (1:3.3.6-15ubuntu2) ...
Setting up libstdc++5 (1:3.3.6-15ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place"

What do i have to do now to get these formats...lol i just am dieing for some music my computer is my only source of it!

---

### Post by aysiu on 2008-04-17
It looks as if they were installed successfully.

Just so you know, for the future, you don't need the terminal to install these things:
[http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree)

---

### Post by AeThEr777 on 2008-04-17
Awesome i got my music! THanx a bunch guys!

---

