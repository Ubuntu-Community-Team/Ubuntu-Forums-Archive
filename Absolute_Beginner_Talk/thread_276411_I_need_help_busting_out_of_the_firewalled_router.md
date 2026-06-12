---
title: "I need help busting out of the firewalled router"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by c0rrupt3d_fate on 2006-10-12
plain and simple, I use windows machines at school, however at school you've guessed it, 99% of the world wide web is blocked, and its blocked at router level, and I can't use a proxy I've tried that already, what I can do contrarily is use a VPN to my house, to get to virtually any site I want, from school.... although the site that was providing the VPN service for me, which by the way was logmein.com is also now blocked, I've heard something about ssh tunneling as an alternative, I have putty on the computer at school, I just can't use it, because I have not the slightest clue on how to go about setting up a server at my house for it, also keep in mind, my only objective here is accessing blocked web pages


thank you in advance

---

### Post by MNCaudill on 2006-10-12
If you have Ubuntu at home and have ran "sudo apt-get install ssh", you are 90% of the way there. You probably also need a semi-static IP address (basically not dialup).

At your house, open up port 22 for SSH. 

Go to [http://checkip.dyndns.com](http://checkip.dyndns.com) from your house. Write your IP  address down.

At school, fire up PuTTy. Under host, put in your IP address of your house.

On the tree in the left pane of PuTTy, select "Tunnels" at the very bottom. 

In that interface, enter in 8008 (I like 8008 ) and tick the Dynamic radio button.

Click add. You should see a "D8008" in the window. 

Now hit connect with putty. A new window should show and you should be able to login with your normal Ubuntu login and password.

Now inside of your browser at school (hopefully Firefox, but IE will work) find where it asks for your proxy info. In Firefox, you go to Tools->Options...->Connection Settings. Click the proxy connection button and inside of the SOCKS proxy, enter in localhost as the hostname and 8008 as the port. Hit ok.

You should be able to browse any site you want now.

---

