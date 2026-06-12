---
title: "Dapper Internet problems"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by hallco on 2006-06-03
I cannot connect to the Internet using Dapper, either from the live CD or after installation. The installation program failed to connect to the Security Updates repository.

I cannot connect to any repository using either Synaptic or apt-get from the command line. I can ping a website and get a response. However no connection to any site using Firefox.

I have no problem connecting to the internet on the same machine using either Mepis or Knoppix live CDs, so I cannot think it is a router problem . In network settings my DNS is correct for my router, and my ISP is automatically connected using DHCP.

Can anyone assist please

---

### Post by steve.horsley on 2006-06-03
Let's concentrate on archive.ubuntu.com. First, can you oing it by number?
  ping 85.133.25.8
Second testing DNS, can you ping it by name?
  ping archive.ubuntu.com
Third, can you connect to port 80?
  telnet archive.ubuntu.com 80

If you can telnet to port 80 by name, then there is really no connectivity issue, and there maybe the proxy settings need checking out. If any of the above fails, post the error message.

---

### Post by hallco on 2006-06-03
Hi Steve. It's awfully nice to receive such a helpful reply. Sorry to have been so long in responding, but have only just got back from the pub having celebrated my 66nd birhday.

Dealing now with your suggestions :-

1. Pinging the number elicits the response of a continuous stream indicating that 64 bytes is being read/received/sent?

2. Pinging the address produces a response (cannot read what I have written here properly because of old age and beer) " could not connect to host", possibly.

3. Telnetting as suggested produces " could not resolve host - temporary failure in name presentation", possibly.

You will appreciate that I am obviously logging on here using the Mepis live CD whatsit and Firefox. Any suggestions?

---

### Post by hallco on 2006-06-03
Sorry Steve, I'm here again to correct the last response. I misread your instructions (failing eyesight) - the correct response should have been:-

2. The same result as in (1) i.e. a message showing a continuous receipt of 64 bytes.

3. "Connected to archive.ubuntu.com '^]'."

So it seems that ping and telnet are working.

Any suggestions?:)

---

### Post by steve.horsley on 2006-06-04
Your networking is OK then. DNS is working because you can connect by name, and TCP connections to port 80 (port 80 is the HTTP port) can connect OK.

I supporst the next step is to use firefox to go to [http://archive.ubuntu.com/](http://archive.ubuntu.com/)
and see what firefox says. We KNOW we can connect there, because you did it with telnet. If firefox can't get there, try Edit->Preferences, go to the General tab, click Connection settings, and make sire it is set for direct tonnectino to the internet (i.e. not using a proxy).  If still no go then I am out of ideas.

What is the error message when you enter **sudo apt-get update**? Can you post the result?

---

### Post by jvictor on 2006-06-04
It looks like a problem with IPV6 to me, 

U can disable IPV6 at /etc/modprobe.d/aliases by doing something like this

#alias net-pf-10 ipv6
alias net-pf-10 off

reboot and u should be ready 

In firefox, type about:config and toggle the value of network.dns.disableipv6

Are u using a static IP ? or do u use DHCP ? Try to use a static IP if the above steps dont work.

HTH

---

