---
title: "New to linux, and cant connect to Router."
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by nickdawg940 on 2006-01-10
Hey am using the "Live CD" because I am still deciding if I should completely switch. One thing I noticed, as I was first checking it out, was that I could not connect to the internet at all. :confused:  I am using a router and an internal wireless card. What "general" info do I need to tell it as I am setting up my config so it might find my router.

---

### Post by d1337 on 2006-01-10
Have you checked to see that your internal wireless card will work with Linux?  I haven't used the Live CD much, so I'm not certain how much functionality you have as far as configuring.  Can you access a terminal and run "lspci" to see if your card shows up?

d1337

---

### Post by blair on 2006-01-10
You need to determine whether you have a physical connection problem, a DHCP problem or a DNS problem. Suggest you run some basic connectivity tests:

1. A basic connectivity test is to ping the router first. This will tell you whether you have IP level connectivity to the first hop. 

2. Open your browser and try to connect to the HTTP server inside the router using the IP address of the router (if your router has a built-in web-based mgt console). This will confirm application level connectivity to the first hop.

3. Ping an Internet host. This will tell you whether packets are getting through the router.

4. web page and internet web site. This will tell you whether DNS is working.

5. Try configuring your interface for static IP versus DHCP.

6. Verify your interface is even active. Some Linux distros require you to manually enable the network interface. 

7. Try a wired connection instead of a wifi connection. If this works you know you have a wireless link problem (e.g. SSID or WEP key problem) or a wifi NIC  driver problem.

---

