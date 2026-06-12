---
title: "Dhcpcd fails durning install"
date: 2009-01-17
forum: Arch and derivatives
---

### Post by .Maleficus. on 2009-01-17
For a couple of weeks now I've been meaning to replace my Ubuntu install with Arch x86_64.  I've got a long weekend so I thought I'd give it a go.  I'm having a pretty big problem though - DHCP is failing to work.  At first I thought it was just a problem with the computer (I don't know why it would be as I installed Arch on it twice before) but yesterday when attempting to put it on my main computer, I got the same error.  On both computers the interfaces appear really messed up during "Configure your Network" (the look like eth0_____0x___ja____34 (not exactly that but you get the idea)).  I'm not really sure what's going on - my main computer has 2 ethernet controllers and both are detected but there aren't any power lights on them and the connection light on my switch is off.  After doing hwdetect --show-net I modprobed sky2 like it asked and still got nothing.  Any ideas?

Thanks in advance guys.

---

