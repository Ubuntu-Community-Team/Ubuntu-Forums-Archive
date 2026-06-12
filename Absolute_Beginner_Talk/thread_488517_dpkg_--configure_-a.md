---
title: "dpkg --configure -a"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-06-30
Hi,
My automatic upgrade won't upgrade anymore.

I keep getting the message 

Only one software management tool is allwoed to run at a time.

Please close the other applications eg aptitude of synaptic.

I also get an error message saying E: dpkg was interrupted. You must run 'dpkg --configure -a' to correct the problem.
Running dpkg --configure -a does nothing.
Running sudo dpkg --configure -a does something.....but nothing of any value. 

Setting up sun-java5-doc (1.5.0-06-1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]


What has gone wrong, and how can I fix it?

Phil Edwards

---

### Post by overdrank on 2007-06-30
> **groeswenphil said:**
> Hi,
My automatic upgrade won't upgrade anymore.

I keep getting the message 

Only one software management tool is allwoed to run at a time.

Please close the other applications eg aptitude of synaptic.

I also get an error message saying E: dpkg was interrupted. You must run 'dpkg --configure -a' to correct the problem.
Running dpkg --configure -a does nothing.
Running sudo dpkg --configure -a does something.....but nothing of any value. 

Setting up sun-java5-doc (1.5.0-06-1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]


What has gone wrong, and how can I fix it?

Phil Edwards

Hi and as for "Only one software management tool is allwoed to run at a time."
That is what it means you can not have synaptic manager or add and remove open at the same time a update is running.
If sudo dpkg --configure -a does nothing then  try and open synaptic manager and fix broken packages, it is located under edit in the options, You may have to search for the broken packages and that options is under settings, filter.
Hope this helps good luck! :KS

---

### Post by groeswenphil on 2007-06-30
Ok

I feel like I'm getting nowhere fast.

I tried the suggestion.
Initially, I got nowhere and then suddenly Synaptic showed a lot of files called dpkg.
So, I picked the big green one with the Ubuntu icon next to it and sellected repair installation.

It sort of started to do its stuff, then a terminal window appeared with exactly the same message as before.

Now, the website mentioned in the error message gives no indication of which file to download to fix this problem.

Any ideas?
Phil

---

### Post by bapoumba on 2007-06-30
Have you been trying to install java?
Please try the procedure detailed [here]("http://ubuntuforums.org/showpost.php?p=1977260&postcount=4").

---

