---
title: "domain not on port 80"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by emprog on 2006-09-13
I recently set up apache web server on my computer but had to use a different port due to my ISP blocking 80. So, at the moment I am using port 84. I also set up a dyndsn account emarquez.homelinux.net which was a success except for one small issue and that is I need to append the port to the end like so.

emarquez.homelinux.net:84

I have tried setting the domain to include the port along with my IP but it cries about the ip being invalid. My question is, how can I go about having emarquez.homelinux.net point to my site without adding port 84 and without using port 80? If there is no way, will the only option be to pay my ISP?

---

### Post by PriceChild on 2006-09-13
I've been experimenting with the same kinda thing lately.  I think that no-ip.com will help you solve the problem using their "forward port 80" feature.  It is free :)  Pricey

---

### Post by emprog on 2006-09-13
You know, that worked perfectly. Using the redirect + mask option not only handles the port redirect for me but also hides the ip once the page loads. Excellent! Thanks for the reply.

---

