---
title: "HOWTO: network printing with Brother HL 1230 and a printserver box"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-09-09
After struggling with this for 4 months, and unsuccessfully following numerous suggestions and postings, as well as contacting Brother technical help to no avail, I have finally solved the problem of printing over an ethernet network  to a print server connected to my Brother HL 1230. Following all of the advice and instructions I found, everything went well EXCEPT that nothing would ever print as the print queue would never empty as the printer is for some reason permanently flagged as busy despite being idle. 

In the end, it turns out the trick is really simple. All you need to do is follow the standard CUPS browser based dialogue for ADD A PRINTER, specifying the following values on the relevant pages:
*printing protocol:* http:
*device URI*- (this is the key value , that had me going crazy) **socket://**<IP_address_of_your_printer>

I don't know why it works;but it does. Anything other than SOCKET in the key position gets you nowhere.

---

