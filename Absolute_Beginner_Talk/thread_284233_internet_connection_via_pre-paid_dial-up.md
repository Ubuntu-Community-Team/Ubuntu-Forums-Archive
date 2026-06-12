---
title: "internet connection via pre-paid dial-up"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by essnell on 2006-10-25
I have receently installed Ubuntu 6.06 and am happy with that.
however I am having problems setting up internet connections. 
problem seems to be that phone connection is pre-paid.

with pre-paid to access internet one has to give the account no and the phone no of whom you are calling. 

this also does not give a dial tone.

with other OS  I use this format in the phone no. 

      ,,,,account no#,,,,phone no#

the comnmas are to give the system time for the talking on the line. 

i have put it in several times but the ubuntu will not retain all of the nos. I cannot see why.

Has anyone any suggestions? I don't want to go back to having a phone bill.

essnell

---

### Post by Bachstelze on 2006-10-25
Your dialup modem is probably a Winmodem, which can be really tedious to install. All you need is on [http://www.linmodems.org](http://www.linmodems.org)

Basically, all you have to do is download their scanMoodem tool, run it and send the text files it will generate to their mailing-list, where nice volunteers will help you to get it working, if at all possible.

---

### Post by essnell on 2006-10-27
Thanks for reply;

The modem is a Dynalink 56k voice fax external serial modem which is connected to com1 ie. ttySO for Ubuntu.
 I had checked it out on the LinModem site as in the online instructions for setting up which I have printed out.

I got the modem working for a couple of times but our dial out phone no. is very long. 

This is because we have pre-paid phone connection. 

I have a 12 digit plus a # access no. then I have the ISP phone no. which has 8 digits plus a # 

The problem seems to be that the backing code cannot handle that many digits. Also I have to give it space for the operator to speak hence  a group of ',,,,' goes in front and between the two nos.

With this there is no dial tone. 

I have this working in XP Pro. and I have to cancel the "wait for dial tone" order.

What I need to know is how to get this long phone number accepted.

It works or at least retains only half of it - hence I don't get connected.
Hope you follow what I'm trying to explain.
Essnell

---

### Post by odin1965 on 2006-10-31
If you are using GnomePPP to dial you can enter a dial prefix and also modem init strings.

I use the dial prefix *70 here in Canada to disable call waiting whan I am using the modem. You should be able to enter your code for prepaid in here, then just enter the number you are dialing in the 'number' field.

---

### Post by essnell on 2006-11-01
Thanks odin1965,

I'll give that a go and let you know the results.
It's 3.11pm over here in OZ so I'll get back later tonight.

Essnell.:-k

---

