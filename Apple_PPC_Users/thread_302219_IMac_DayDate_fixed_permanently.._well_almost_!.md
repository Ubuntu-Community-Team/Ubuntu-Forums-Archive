---
title: "IMac Day/Date fixed permanently.. well almost !"
date: 2006-11-18
forum: Apple PPC Users
---

### Post by Radiolad on 2006-11-18
Well, I used the Day/Date bug fix as shown below which works fine.
I have replaced the old battery (3.6 volt 1/2AA type) with a brand **new **one (tested and giving a healthy 3.6 volts as opposed to Nil on the old battery)
I restarted the iMac and used the bug fix (below) to initially set the Day/Date.  Ubuntu came up great. I went into the Day/Date option (windows style) just for 'comfort' to see all was well which it was.  I then shut-down the iMac, waited for a couple of minutes and switched it back on hoping to sail through into Ubuntu. NO SUCH LUCK...the same errors came up on screen as per before!
  So can anyone help ... **please **](*,) ](*,) 

BUG FIX:-
[COLOR="SeaGreen"]Boot to the point of the brown screen, then press crtl+alt+f1 (ctrl-option-F1 on a Mac) to get a terminal, and log in. Type: 
 date  
if you get something like 
 Fri Jan 11 19:11:32 GMT 1970  
then run the command 
 sudo date -s "Fri Nov 11 19:11:32 GMT 2005"  
(you will need to put in your password) 
now do the command 
 sudo /etc/init.d/gdm restart  
and hopefully you can log in[/COLOR]

[COLOR="Black"][/COLOR]

  Cheers in antisipation of a resolution,  Radiolad

---

