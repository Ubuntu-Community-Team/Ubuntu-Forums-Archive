---
title: "modem"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by richard willacy on 2005-12-31
:confused: got this problem with my protacol (tcp/ip) address,
now i have done the ip address ok
now i have done subnetmask ok 
but now i cant do the default gate way because i dont know where it is, help on this subject,
preferred dns server need help
alternative dns server need help, thank you for your help richard

---

### Post by coredump on 2005-12-31
You can find out your default gateway and DNS info from the same source that you got your IP address from.  That is, if you got your IP address from an ISP, then the ISP (Internet Service Provider) can also tell you the gateway and DNS info.

If you're making up your own IP addresses, then you'll have to work out the gateway and DNS info too.  The default gateway is the IP address of the machine that connects your local network to the Internet (if you have one).  For a broadband setup, that's most likely your broadband modem, or it could be a firewall machine.  As for DNS, that one must come from the ISP that provides your Internet access.

If you have no broadband access to the Internet, and you're using local IP addresses, then you can leave the default gateway blank.  Your machine won't be able to route packets to the Internet, but since you have no Internet connection, that's OK.  Same goes for DNS, you can leave it blank but you'll have to use numeric IP addresses instead of names.

---

### Post by bscbrit on 2005-12-31
Richard,  the gateway address that is input to the computer is the address of your ADSL modem/router - which I think defaults to 192.168.1.1 in your case.  Sorry I cannot give you more time but I am on a friend's computer and he only has dialup access.  It would not be polite for me to visit, use his computer and run up a telephone bill, and then leave....  I only check the forums briefly each day.

EDIT.  For example, your computer will be 192.168.1.2, your ADSL modem/router will be 192.168.1.1,  your DNS servers will be as given to you by your ISP.

---

### Post by richard willacy on 2005-12-31
i think that i need a lot of help in trying to get this linksys modem/ router to work, been into network settings
and have not got a clue what im looking at, i have set up my ip address 192.168.238.238 then 
subnet mask 255.255.255.0 then the default gateway 192.168.1.1 but every time i do this it says there is this other thing using this ip address, like my skystar2 pci satellite card and its saying to me that it wants a new ip address but how do i make one, and other peolpe on this website are loving it but i cant seem to get anywhere, but i have not given up because i know it will work some time, thanks richard

---

### Post by coredump on 2005-12-31
Did you just make up that IP address 192.168.238.238?  Because if so, you'll need to make up another one which begins 192.168.1., otherwise your PC is on a different subnet from your default gateway.  Your default gateway must be on the same subnet as your PC.

If that IP address is correct, then your default gateway must be at address 192.168.238.something, in order to be on the same subnet.  Can you find out the IP address of your Linksys modem/router?

---

### Post by richard willacy on 2005-12-31
how do i find linksys ip address on my modem:confused:

---

### Post by bscbrit on 2006-01-01
According to the manufacturer's blurb, I believe that the modem defaults to 192.168.1.1, hence my suggestion that Richard enters 192.168.1.2 as his computer IP, and gives 192.168.1.1 as the gateway.
Richard, the paperwork that comes with the modem will tell you what its IP address is; it can be changed but I would recommend against doing that until you have a working network and you know why you want to change the default IP to something else.  In your particular case, I cannot think why you should even want to contemplate changing it.  Can you also confirm that you have purchased the modem/router that you were looking at before Christmas?

---

