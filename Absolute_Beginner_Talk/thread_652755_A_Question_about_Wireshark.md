---
title: "A Question about Wireshark"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-12-29
I'm not sure if this is the proper place to post this, but regardless:

I'm trying to understand how this packet sniffer works.  I know i can press capture and it will show me every single packet that enters and leaves my computer, but that's useless, as there are so many it is next to impossible to decipher them. 
It is my understanding, that if i send someone a message on pidgin for example, it should send them a packet of the text i want to send them... sort of. Is this correct?
How do i tell my packet sniffer (wireshark) to only capture packets coming from one particular program.  And, is wireshark capable of sending packets, or just reading them?

Thanks

---

### Post by dim_hyder on 2007-12-29
Once you've finished the capture click on the search button (mognifying glass icon on the toolbar).

Under find change the type to string and tyoe in the string you are looking for.

I tested this for my pop3 mail account though a mail client. The username and password appeared in clear text as whole strings in a complete ethernet frame.

I did the same with telnet but the results were a single charachter in each frame - you put each frame together and get the password. I think this is because you are actually connected to the remote box via telnet so the connection is always open and is being logged by wireshare whereas the mail client has the username and password details saved and sends the details in one go.

I have never used pidgin, so can't comment but I would think it has more to do with the underlying chat protocols e.g MSN or ICQ.

Dim Hyder

---

### Post by jordank on 2007-12-29
when you say to enter the string I'm looking for, what do you mean?
like if i send a message in pidign i would search for the message i just sent?

example
in pidgin i send a message "hi"
i would search for the string "hi"?

also can you create and send packets in wireshark?

---

### Post by ghostdog74 on 2007-12-29
you installed wireshark without [reading up]("http://www.wireshark.org/docs/") how to use it?

---

### Post by jordank on 2007-12-30
i must be crazy, eh?

---

### Post by jordank on 2007-12-30
One question still remains.  Can wireshark send packets?

---

### Post by Maxtorm on 2007-12-30
This is from recollection as I don't use Wireshark under Ubuntu, but I don't believe it has packet injection functionality. There are a number of other security tools that focus on injection, whereas Wireshark's primary purpose is monitoring. 

One other thing that you may find handy (and undoubtedly will also find in the above-noted documentation): when you're viewing the capture output, you can right-click on any TCP packet and then select "Follow TCP Stream" (or something like that) and Wireshark will reassemble the entire TCP conversation for you without you having to open each packet individually.

---

