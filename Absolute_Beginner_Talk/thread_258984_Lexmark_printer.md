---
title: "Lexmark printer"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by LookTJ on 2006-09-16
ok i got a model E312L

it's a windows network printer(desktop)

I'm trying to add a network printer on ubuntu(laptop)

So any help? Thanks

~Taylor

Edit: oh and E312L isn't on the list, only E312

~Taylor

---

### Post by LookTJ on 2006-09-16
no one knows?

---

### Post by orb9220 on 2006-09-16
Lexmark are notorious for being linux unfriendlly.
And being the crapiest of all printers.

Try searching forums using lexmark as search term.

---

### Post by YeahBuntu on 2006-09-17
Hmmmm Lexmark are good printers BTW otherwise people wouldnt be asking for help adding them to their Linux

I have the Optra E312L

Connected to my router's printer server.

You need to know the location of where the printer is.  Do you have a windows OS also connected to the lan that you can get the IP address from?  

Once you have the IP addy click:

System>> Administration>> Printing    (this assumes you are using GNOME desktop)

Click Printer at the top then Add printer

ON the drop down menu choose Unix/???  (cant remember what the other one is)

Choose network printer and then put the IP addy of your printer in the box.

It should find it and be able to print to it.

---

### Post by orb9220 on 2006-09-17
"Hmmmm Lexmark are good printers BTW otherwise people wouldnt be asking for help adding them to their Linux"

No the are the cheapest in price and quality. People have them because they are bundled with so many system bundles. And are rebadged for Dell,Compaq,etc.

This is widely know thru out the computer world.

---

### Post by LookTJ on 2006-09-17
> **YeahBuntu said:**
> Hmmmm Lexmark are good printers BTW otherwise people wouldnt be asking for help adding them to their Linux

I have the Optra E312L

Connected to my router's printer server.

You need to know the location of where the printer is.  Do you have a windows OS also connected to the lan that you can get the IP address from?  

Once you have the IP addy click:

System>> Administration>> Printing    (this assumes you are using GNOME desktop)

Click Printer at the top then Add printer

ON the drop down menu choose Unix/???  (cant remember what the other one is)

Choose network printer and then put the IP addy of your printer in the box.

It should find it and be able to print to it.didn't work for me

---

### Post by Melcar on 2006-09-21
> **orb9220 said:**
> "Hmmmm Lexmark are good printers BTW otherwise people wouldnt be asking for help adding them to their Linux"

No the are the cheapest in price and quality. People have them because they are bundled with so many system bundles. And are rebadged for Dell,Compaq,etc.

This is widely know thru out the computer world.



I feel that I must, in good conscious, defend what is a good and reliable brand.  Before making the venture into Linux, I made a point of changing all my house (and office) printers to Lexmark models.  They have all performed exceptional, specially in the office were they are used heavily.  In my opinion they are the most robust and reliable printers, surpased only by HP.  However, they suck majorly when it comes to Linux.  I have simply given up trying to make them work perfectly over a network.

---

### Post by YeahBuntu on 2006-09-21
Hmmm I just dont understand why you'd be having such difficulties.  I presume maybe its the router?  My router handled the connection to the E312L printer (and my linux box here) just fine.  No problems.

---

### Post by Sef on 2006-09-21
Linuxprinting says the E312 works perfectly.  [Lexmark 312]("http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Optra_E312") (This may give you an idea of what else to do.)

---

### Post by blx_286 on 2006-09-21
> **Melcar said:**
> I feel that I must, in good conscious, defend what is a good and reliable brand.  Before making the venture into Linux, I made a point of changing all my house (and office) printers to Lexmark models.  They have all performed exceptional, specially in the office were they are used heavily.  In my opinion they are the most robust and reliable printers, surpased only by HP.  However, they suck majorly when it comes to Linux.  I have simply given up trying to make them work perfectly over a network.

Not trying to start a Lexmark bashing thread, but I have to agree with Orb9220. Lexmark is evil and will kill your dog. If you don't have a dog, they will send you one for the sole purpose of killing it.

I had 3 Optra SE3455's on my network. The bossman bought them because they were cheap. Then after they suckered you into buying the thing, they try to lock you into buying toner just from them. See [http://www.drmwatch.com/legal/article.php/3095371]("http://www.drmwatch.com/legal/article.php/3095371")

I have HP's with over 3 million copies and they are still running strong. Maintenance costs have also been cheaper on the HP's.

I am a Linux noob but if it's an IP printer, can't you print to it with CUPS or something and using a RAW format?

---

### Post by Melcar on 2006-09-21
> **blx_286 said:**
> Not trying to start a Lexmark bashing thread, but I have to agree with Orb9220. Lexmark is evil and will kill your dog. If you don't have a dog, they will send you one for the sole purpose of killing it.

I had 3 Optra SE3455's on my network. The bossman bought them because they were cheap. Then after they suckered you into buying the thing, they try to lock you into buying toner just from them. See [http://www.drmwatch.com/legal/article.php/3095371]("http://www.drmwatch.com/legal/article.php/3095371")

I have HP's with over 3 million copies and they are still running strong. Maintenance costs have also been cheaper on the HP's.

I am a Linux noob but if it's an IP printer, can't you print to it with CUPS or something and using a RAW format?


It's all preference really.  Lexmark and HP are my brands of choice and I will stick to them.  As for the printing issue, I am able to do simple printing over a network, but sometimes the machines will not respond.  Oh well, we'll be changing office locations soon and I plan to re-do the whole computer network and make it more Linux friendly.

---

### Post by blx_286 on 2006-09-21
> **Melcar said:**
> It's all preference really.  Lexmark and HP are my brands of choice and I will stick to them.  As for the printing issue, I am able to do simple printing over a network, but sometimes the machines will not respond.  Oh well, we'll be changing office locations soon and I plan to re-do the whole computer network and make it more Linux friendly.

True, everyone's mileage will vary. I just got really put out with the toner issue, due to the volume of printing we do (or did). At one time we really were going through alot of trees.

All of that being said, I am having a problem printing to my networked HP 4M :rolleyes:. Prints one line of garbage and then runs all the paper out of the tray.

---

