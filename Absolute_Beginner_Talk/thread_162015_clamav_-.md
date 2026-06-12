---
title: "clamav -"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by Wyrm_1972 on 2006-04-18
Hi, have succesfully got ClamAV and Evolution checking my incoming email as direct in this thread...

[http://ubuntuforums.org/showpost.php?p=610408&postcount=6](http://ubuntuforums.org/showpost.php?p=610408&postcount=6)

And am now trying to understand the bash script I used to do it all. I've pretty much got a handle one evrything bar this...

clamdscan - 1>$FILE

Worked out what the 1>$FILE does, but what does clamdscan - do? Specifically the - in a bash script?

Any light to shed on this. Just trying to understand is all.

---

### Post by meborc on 2006-04-18
i dont have clamav, but as far as i know clamdscan is a bin file... kind of similar to exe in windows... so it is the program file making the scan...

but i might be shooting wide here

---

### Post by macdo on 2006-04-18
Try [http://www.tldp.org/LDP/Bash-Beginners-Guide/html/](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/)

Have fun!

---

### Post by Wyrm_1972 on 2006-04-18
[QUOTE=macdo]Try [http://www.tldp.org/LDP/Bash-Beginners-Guide/html/](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/)

Have fun![/QUOTE]

Have done... that's where I get confused... in there it states it expands to the flags used upon invocation... however, I also read on another site that it needed to be used with ClamAV to make it read from a data stream. 

Which is correct?

---

