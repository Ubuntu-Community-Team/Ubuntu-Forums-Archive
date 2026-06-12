---
title: "connecting to shared folders on windows xp machine"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by angelsneverdie on 2006-12-29
Here's the latest adventure of me trying to learn linux:

I have no problem getting files from the shared folder on my ubuntu machine to my windows machine.

getting to my windows machine from my linux machine however is a different matter.  

i press alt+f2 and type in the IP of my windows machine, smb://192.168.1.100

a window opens up listing all the shared folders . . . so far so good.  There's one folder that I double click on and it opens and i can get files and all is good.  when i try to open any of the other shared folders a window pops up and says:  "you must log in to access guest@192.168.1.100/My Pictures domain WORKGROUP
then it has spaces for username, domain, and password.  It also has check boxes for 'remember password for this session. and 'save password in keyring.'  the two button choices are cancel, and 'connect'.

no matter what i try i can not get through this window.  anyone know what i need to do?](*,)

---

### Post by chipdip on 2006-12-29
Log in?

---

### Post by ArtechnikA on 2006-12-29
just a thought - is your Linux box in the same workgroup as your Win box?
My guess is no, so it's trying to do the domain controller thing.
If your Win box is actually set up with domains, rather than just a workgroup, you are beyond my ability to suggest anything...

---

### Post by angelsneverdie on 2006-12-29
no matter what i type in for username or password - nothing is correct.  why can i access one folder without being prompted for this crap?  how do i get the other folders to behave like that one?  

and as far as arechnika's question about not being on the same domain - i'm not really sure what that means but all i can say is that i can access files in one of the folders . . . so theoretically everything should work?

thanks

---

### Post by ArtechnikA on 2006-12-29
> **angelsneverdie said:**
> no matter what i type in for username or password - nothing is correct.  why can i access one folder without being prompted for this crap?  how do i get the other folders to behave like that one?  

and as far as artechnika's question about not being on the same domain - i'm not really sure what that means but all i can say is that i can access files in one of the folders . . . so theoretically everything should work?

not domain, workgroup...

but yes, if you can get to anything, that's probably not your problem.

so - check the permissions on the share on the Windows box - maybe it was set up to require a password...

---

### Post by angelsneverdie on 2006-12-29
i've checked the permissions and can't see any difference between the working shared folder and the non working shared folders on the xp machine. . .

i wish i knew more about this stuff . . . it is probably something simple i'm not getting. . .

---

### Post by angelsneverdie on 2006-12-31
well i solved the problem by just moving files i wanted into the folder that worked.
which worked for about a day, i moved a file of pictures into that folder, and now when i try to open that folder it says i do not have permissions to view the contents.

slightly different issue, any ideas?

---

### Post by Mung the Wicked on 2008-01-12
This will happen with two or more  Windows XP machines.  Sometimes it's easy and sometimes it's hair-pulling depending on the situation. I don't think it's your Ubuntu machine.   In my previous job, as a tech primarily servicing Windows machines, I'd run into this problem here and there.

Typically, if you want to network some Windows XP machines together, you assign them to the same Workgroup.  Computers in the same Workgroup can be accessed through My Network Places.  This is a simple way to network XP machines.  A domain involves a server (like Server 2003) acting as a domain controller.  XP Pro machines can join domains, but not XP Home if I recall correctly.  Domains are more complicated.  I'm guessing you're dealing with just a Workgroup.

On one of my XP machines here at home I have a folder (actually several) that is shared.  Other computers within the Workgroup can access this folder as long as I gave permission for those computers on my network and within that Workgroup the ability to read and write to that folder.  An Ubuntu machine should be able to see and access this folder as well.

Have you tried: {
1.) (In XP) Right click on the folder in question.
2.) Click on Properties.
3.) Click on the Sharing Tab.
4.) Check "Share this folder on the network".
5.) Check "Allow network users to change my files".
}

Here's a possible helpful link for you:
[http://support.microsoft.com/kb/304040](http://support.microsoft.com/kb/304040)
[http://support.microsoft.com/kb/308421](http://support.microsoft.com/kb/308421)

Sometimes though, I'd experience this bizarre situation where I'd be in My Network Places with a customer's PC while trying to access a shared folder or printer on the customer's "main" PC.  It would ask me for that stupid log in.  I don't remember how exactly I fixed this, but I remember going through all sorts of hoops and hurdles.  I recall even performing a fresh install of Windows XP (among other things) and the problem still persisting.

This hair-pulling situation can be described adequately by:
[http://help.lockergnome.com/windows/access-shared-folder-network-ftopict448288.html](http://help.lockergnome.com/windows/access-shared-folder-network-ftopict448288.html)

Time and moving on to a programming job has caused my memory to forget the ultimate solution, but I figured that would give you some helpful insight.  It has something to do with the Windows XP machine that you're trying to connect to.

So, these two scenarios should cover your problem.  One is easy, and I hope it's that one.  The other is a pain in the butt.  I hope this helps you out.

---

### Post by bolchisbolchis on 2008-03-02
Try enabling "Simple File Sharing":

1. press Win+E for explorer
2. click "Tools" on main menu
3. select "Folder Options"
4. enable "S F S"(last option on the bottom)

Then try to open the folder's properties and in the "Sharing" tab, enable "Share this folder" and enable "Allow network users change my files".

P.S. Also have your workgroup name changed to the same name as the XP machine.

---

