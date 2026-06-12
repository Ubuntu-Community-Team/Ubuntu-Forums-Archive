---
title: "d-link"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by richard willacy on 2005-12-20
got this d-link and streat away got trouble,first thing i did is to connect the blue wan cable to the pc wan socket,then to the d-link router and all is ok with what if done so far,got power to the d-link, then put in link
cd and nothing happens you get these 3 things and thats it nothing els happens,it says that i have to use
the setup wizard and you have to connect to this address [http://192.168.0.1](http://192.168.0.1) but every time i go to that adress
i get no where,i have tried all sorts of ways to connect to this setup wizard but nothing works,any help please
richard:confused:

---

### Post by jeremyk on 2005-12-20
Hi,

I got a similar problem a while ago. 

Let say that your interface is eth0, do the following:

sudo dhclient eth0 (replace eth0 by the releavant eth#n)

Then go to [http://192.168.0.1](http://192.168.0.1)

with firefox, and then use the wizard.

The first should make the second work.

Cheers,
Jeremy.

---

### Post by richard willacy on 2005-12-20
d-link, tried what you say and it did come up with lots when i went into terminal and typed sudo dhclient but could not find anything like etho,this morning i got this d-link router through the post,now at the moment i am using windows xp home and i have never used this ubuntu before so any help would be good,and i thought 
that if you buy somthing you get this cd and your off, but this cd does nothing and im sopposed to go to this website and sign in then use this wizard,but cant because its not there and am i suppose to use linux with this d-link or windows, and i have done everything ok i think,lets go though this a gain first i put blue wan 
cable into the wan socket on stack then other end into the d-link and thats it nothing els,there is not a connector what goes into the modem because its got one usb going into the usb connection on the stack then into the usb part on the voyager modem,hope its right, and this is my first time on this linux and i have not even gone out yet so anu help would be good thank you richard

---

### Post by richard willacy on 2005-12-20
rj45 got this phone line cable going to my modem, can i use one of these rj45
and just plug it into the d-link and will it work:confused:

---

### Post by richard willacy on 2005-12-20
when i get my D-LINK, to work right,how to get out onto the internet, how do i go about it, and speaking of my d- link i think that im out on the net because in one part of this ubuntu there is some numbers and a packet,
and these numbers keep changing a bit like when using windows but this is ubuntu linux and if im ok how to put first thing onto my desktop:confused:

---

### Post by bscbrit on 2005-12-20
Richard
I've just got home from work and seen your series of messages! What make and model of modem/router have you got?  What have you done so far?

---

### Post by richard willacy on 2005-12-20
hi there bscbrit, just got my router this morning and this is what if done so fare, put the blue cable into the back of my computer stack into the lan socket, and other end into the router thats it nothing els, now the modem i have got is voyager 105 usb adsl,now the light on the router keeps going of and every time i turn the pc on its saying there is cable loose or somthing,and the modem only has on phone connector and a usb
connector, what do you think,have i got it rong

---

### Post by richard willacy on 2005-12-20
name of router d-link di-604 model

---

### Post by bscbrit on 2005-12-20
Hi Richard,  I thought that you were replacing you BT Voyager with a new combined modem/router.  What make and model of router have you bought.  Depending on the model, you might not need you BT Voyager anymore but I need to have more details before I can say for certain.

---

### Post by bscbrit on 2005-12-20
Richard, I know that we have had problems setting up your BT Voyager modem.  Did someone help you to get it working?  The d-link di-604 will share an existing modem connection with up to 4 computers - but you need a working modem to use it.  Is your BT Voyager modem now working under linux?

---

### Post by richard willacy on 2005-12-20
ok bscbrit this what if got, d-link di-604 express ethernetwork,broadbandrouter,the router acts as a dhcp server and will assign,all the necessary ip address infomation on your network,yes i was going to get new modem but i thought that a router world do the trick but if it does no then i will buy new modem after christmas

---

### Post by bscbrit on 2005-12-20
[http://www.dlink.com/images/products/DI-604/DI-604_diagram.jpg](http://www.dlink.com/images/products/DI-604/DI-604_diagram.jpg)

If you look at the diagram in the link, you will notice that the router dl-604 is connected to a modem in the top left of the picture.  Your current modem is the BT Voyager 105.  _If_ your modem is now working, you could connect it to the WAN socket on the rear of the router, and plug cables to up to 4 other computers into the remaining sockets.

BUT, if your modem is not working, then you do not want a dl-604, but something like the dl-504t which is a modem _and_ router.  Or you could buy a separate modem, but I think that a combined unit would be cheaper.  Whether you buy this particular model or a different brand doesn't matter. 

Let me know if your modem is now working please.

---

### Post by bscbrit on 2005-12-20
Richard,  contact the shop where you bought the dl-604.  They might be prepared to exchange it for a combined modem and router.  If you wait until after Christmas, they may refuse to do so because you will have had the router for several weeks.  If you 'phone them now you will have at least told them that you have purchased in error.

I am not a lawyer!  You may have other rights to return the goods but I do not know.  I believe that a combined modem and router would be your best bet because it would solve your current problems with regards to getting an internet connection, and would provide you with expansion potential.  But all you really need is a DSL modem that can be set up easily under Ubuntu/linux with the minimum of assistance from others.  Either an ethernet or external serial/parallel modem would meet this requirement.  But there are other possibilities - you might want to ask the advice of other users before you commit yourself.

Whatever you buy, I am sure that we will still be here to help you when you want to get online.

---

### Post by richard willacy on 2005-12-20
no its not working it looks like i have bought a turky so i will see what new year brings, i was going to get new modem but changed my mind, but now i know what i want and will get new one in new years sales,you dont know if pc world does them,cant send it back the box was put into dustbin

---

### Post by bscbrit on 2005-12-20
Richard, if you take the router back without its box, PC World _might_ be persuaded to take it back.  The worst they can say is 'no' - and then you would be no worse off than you are now so there is nothing to lose.

---

### Post by richard willacy on 2005-12-20
yes thats ok but i did not get it from pc world and the shop will not take things back which have no boxes anyway its cost me £30 and you never know it may come in handy some time and i would just like to say a big thank you for all the help you have given me and i will be back with new modem/soon

---

### Post by richard willacy on 2005-12-20
which modem should i get to go with my d-link router, its a bit confusing because with all these modems and routers,which one is good for what im doing,the thing what i want to do is get my ubuntu linux working and i cant because the modem i have is no good so im asking you which one would you buy if you was in my foot steps,the modem i have is voyager 105 usb, now can i do away with the usb part or do i have to stick with usb, i dont know do you:confused:

---

### Post by bscbrit on 2005-12-20
Richard, of course I can recommend a modem, router or combination of the two.  But I am reluctant to do so because I do not want you to feel that you have to spend money on whatever I recommend.  At the end of the day, it will be your money and you need to be happy with your purchase.
There is a modem/router produced by d-link called the DSL-504T.  It will do everything that you want and more, but it is more than you actually need.  However, I cannot see a simple DSL modem from this company.  If you purchase this it will mean that your recently purchased dl-605 router will no longer be needed.
There are lots of suitable modems for sale from other manufacturers but I am in Gibraltar and you are in the UK(?).  I do not know what is a good buy in the UK or what is even available close to where you are.  Ideally, you would benefit from going into a shop that can provide you with sound advice without trying to persuade you to spend more than necessary - such shops are not always easy to find.
All you want is a DSL modem that has either an ethernet connection to the computer, or has a serial or parallel connector.  The reason that I specify these is because there is good support for these in linux / Ubuntu and they are easy to configure.
Many (but not all) other modems use USB (some of which can be difficult to use with Linux), or are internal modems which rely on windows software to make them work.  Again they can sometimes be persuaded to work under Linux but I think from the content of this thread that you would appreciate something that can be made to work fairly easily i.e. you are _not_ looking for a technical challenge but something that will get you online quickly and without great expense.
Perhaps some UK based forum members can offer suggestions?

---

