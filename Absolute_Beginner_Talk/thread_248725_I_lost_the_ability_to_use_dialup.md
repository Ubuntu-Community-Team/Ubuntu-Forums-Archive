---
title: "I lost the ability to use dialup"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by aclamb on 2006-09-01
I think my frustration has caused me to go brain-dead.....
-I just installed kubuntu
-I have been slowly researching topics as I encounter them
-I (finally) got ppp/dialup working (but I was using terminal
mode for login at the ISP - I hadn't figured out how/where to
create the script)
-I got on line using this method and found some references to
pppconfig. I tried that hoping that there would be a 'guided tour
to the logon script'
-I set up a new acct using pppconfig.
-now my original method of 'log on' has quit working. The error messages are the same as when I had AUTH enabled (the original prob) in /etc/ppp/options  (it is not now enabled)

So now that I have screwed this up, any suggestions as to how I fix it (short of a reinstall;) )? 

thanks!

---

### Post by croak77 on 2006-09-01
Have you tried using kppp?

---

### Post by aclamb on 2006-09-01
yes, that is actually what I'm talking about - sorry I wasn't
clear. I am using kppp. I have set up an account for my ISP. I had selected terminal mode because I thought I would have to have a login script - I obviously know just enough to be dangerous. 
I did some more searching since the post. I found that if I
added "noauth" in the arguments tab of kpp that it was supposed to override other settings in other places. I changed the login protocol to PAP. Now when I try to connect it still fails but
The error message has changed to "using noauth requires root privileges" when I try to connect.

---

