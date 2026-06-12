---
title: "Setting up a VPN"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-11-06
Hi there,

I have no idea what I'm doing and googling just confused me more! :)

I need to Setup a VPN network with my University and I've been at this for hours!

The Varsity uses IP-Sec and gave me a URL: contivity.wits.ac.za , and IP address, 146.141.3.2 and a user ID and Password.

Now, what daemons need to be running and what application works bets because I've tried a couple and I can't get anything to work!  

Thanks for any advice or a a point in the right direction,

Rudolf

---

### Post by cmnorton on 2007-11-06
I'd do this in stages. First, see if you can connect to a regular old network, wireless or otherwise.

Also, which version of Ubuntu is this, and what kind of networking hardware does your Ubuntu system have?

---

### Post by RudolfMDLT on 2007-11-06
It's meant for my laptop but at the moment I'm first trying to get my desktop to work over ADSL. Both machines are running 7.04.

EDIT: I have attached a KVPN screen for vpnc, could you just maybe tell me what goes where. Whats IP-Sec ID VS VPN-gateway?

---

### Post by Fire_Chief on 2007-11-06
Have you tried configuring a new VPN connection through Network Manager? It's fairly straightforward and sometimes it "just works". Unfortunately, my vpn experience is limited to connecting to Cisco VPN devices. This one is a Nortel VPN concentrator. It *should* still work though. Do you know how another user is configured to connect to the VPN? Does the university IT group have a help page or FAQ on setting up the VPN client connections?

---

### Post by cmnorton on 2007-11-06
If your desktop is wired, Network Manager should be able to take care of this. If you desktop is wireless, others have but I have not been able to have Network Manager connect me using its method. I don't quite understand how it works, but it works fine on a wired network. 

As I stated in my previous post, concentrate on non-VPN first.

---

### Post by RudolfMDLT on 2007-11-06
> **Fire_Chief said:**
> Have you tried configuring a new VPN connection through Network Manager? It's fairly straightforward and sometimes it "just works". Unfortunately, my vpn experience is limited to connecting to Cisco VPN devices. This one is a Nortel VPN concentrator. It *should* still work though. Do you know how another user is configured to connect to the VPN? Does the university IT group have a help page or FAQ on setting up the VPN client connections?

Yes they do give help... for windows! I'm having great fun - now Kvnpc keeps crashing! How did you configure your Cisco VPN?

@cmnorton

What do you mean Non-VPN,  I am connected to the Internet via ADSL and now I need a VPN connection? Sorry if I'm being daft! :$

Thanks,

Rudolf

---

### Post by Fire_Chief on 2007-11-06
The fact that the setup help is for Windows is okay. We just need to know what information they are configuring on the Windows side client. Translating it for use here should be pretty easy...could you post the link to that page?

I was unable to get vpnc to work for connecting to a Cisco VPN concentrator on my system...I ended up using the Cisco VPN client for Linux with the gvpndialer frontend.

---

### Post by RudolfMDLT on 2007-11-06
Busy using Network Manager:

I rightclick, point to VPN, click add, follow the prompt and when I click apply, nothing happens. It doesn't add is and when it does it forgets that it added it when you come back. I've tried starting Networkmanager as root and that doesn't work either.

Thanks for spending the time on this headache! :)

Rudolf

---

### Post by RudolfMDLT on 2007-11-06
It's a word document with 4 pages on how to install a VPN client and on the 5th page:

> Nortel VPN Client Configuration

Once the client is extracted and installed, launch it and create a new connection profile...

1) Enter Wits as a connection profile name (you can leave the description blank if you like)
2) Select "Username and Password" radio button for Authentication Type.
3) Enter the Username and password as given and check the Save Password box if you like.
4) Select the "No, I don&#8217;t have a group password" radio button.
5) Enter contivity.wits.ac.za for the Destination
6) If the user is using a dial up modem, then select "Yes, I want to make a dial up connection first". All other permanent connections (ADSL etc) select "NO".
7) Click finish to complete.

When logging in the first time, users will have to change their passwords (as a security measure).


I went to the URL that they gave us as the download and browsed around a little and found this as well:
> Mac OsX VPN Account Setup

1.Click on &#8220;Go&#8221; &#8594; &#8220;Network&#8221; and then open &#8220;Internet Connect&#8221; (from the Dock)
2.From &#8220;Internet Connect&#8221; click &#8220;File&#8221; &#8594; &#8220;New VPN Connection&#8221;
3.Select &#8221;PPTP&#8221; and then &#8220;Continue&#8221;
4.Click on the arrows next to &#8220;other&#8221; in the &#8220;Configuration&#8221; field and select &#8220;edit configurations&#8221;
5.From the Edit Configurations screen, enter
I.In the &#8220;Description&#8221; field enter any name that will help you identify the connection
II.In the &#8220;Server Address&#8221; field enter 146.141.3.2
III.In the &#8220;Account Name&#8221; field enter the account name given to you (usually your staff/student number)
IV.In the &#8220;User Authentication&#8221; field, make sure the password radio button is selected.
V.In the &#8220;Encryption&#8221; field select &#8220;Maximum (128 bit only)
6.Click &#8220;OK&#8221;
7.Enter your password and click connect to make a VPN connection

also, the URL: [http://uamp.wits.ac.za/vpn/](http://uamp.wits.ac.za/vpn/)

I'm going to boot into windows quickly and see whether this actually works.

---

### Post by RudolfMDLT on 2007-11-06
Well - it took less than 1 minute to get it working in XP... sigh.

---

### Post by RudolfMDLT on 2007-11-06
How can I turn off the Firewall in Ubuntu? Is there one installed by default?

---

### Post by jackhynes on 2007-11-06
> **RudolfMDLT said:**
> How can I turn off the Firewall in Ubuntu? Is there one installed by default?

Okay I'm doing the exact same thing as you. My uni also only gives instructions to Windows/Mac users, can't seem to figure out how to get the VPN working...

---

### Post by jackhynes on 2007-11-06
> **Feisty/Edgy x86**

You will need NetworkManager installed:

```
sudo apt-get install network-manager-gnome network-manager-pptp
```

Then, a network icon will appear in your notification area. Select it, and then select VPN Connections > Configure VPN. Add your VPN to the list, and then in the terminal do the following:

```
sudo NetworkManager restart
```

Click the icon again, and go to VPN Connections and then select your VPN. Voila. You're connected!

This does what it says but I'm still not sure if I'm connected as I haven't been asked for user name / password.

**Edit:** Work perfectly now, I don't think I restarted the Network Manager. Now I can connect using File>Connect to server then selecting Windows Share and it connects to my smb share.

---

### Post by RudolfMDLT on 2007-11-06
How'd you get it to work? Could you maybe give me some details as to what you did? I would really appreciate it! Thanks!

---

### Post by jackhynes on 2007-11-06
> **RudolfMDLT said:**
> How'd you get it to work? Could you maybe give me some details as to what you did? I would really appreciate it! Thanks!

Okay this is exactly what I did (using Gutsy + wireless):

In the terminal:
```
sudo apt-get install network-manager-gnome network-manager-pptp
```

Click on the Network Manager in your system tray, then go to VPN connections and click 'Configure VPN'. Click 'Add' then click Forward twice. I named my connection 'Aber VPN' and typed 'vpn.aber.ac.uk' in the Gateway box. Click Forward then Apply.

Then in the terminal:
```
sudo NetworkManager restart
```

Click on the Network Manager again then go to VPN connections and select the new VPN connection. It will connect and a lock sign will appear on the Network Manager icon.

Now open Nautilus and click File > Connect to Server. My university is using Samba for our file sharing so I select 'Windows share' at the top then typed:
```
Server: smb3.aber.ac.uk
Folder: xxx
Username: xxx
```
Replacing the server and the xxx's with your login name (both should be the same).

My University drive then appeared in Nautilus, I double clicked on it and got a password prompt which I entered my uni login and that was it.


You just have to enter your uni network details which will probably be your Windows documentation. Hope this helps.

---

### Post by RudolfMDLT on 2007-11-06
It seems you use PPTP, I've had limeted success using Kvpnc when using pptp but never an actual connection. My university uses IP-Sec. I'm upgrading to 7.10 tomorrow - though i need the vpn connection to download it.

Anyway - I've encountered more bugs than actual solutions so I'm giving this up for a bad job and hoping the a new fresh Ubuntu will be more co-operative! :)

Thanks for all the help! I'll see if any of it comes in handy tomorrow! I really appreciate you time guys!

Cheers,
Rudolf

---

### Post by cmnorton on 2007-11-06
By non-VPN, I mean start with the simplest connection.

---

