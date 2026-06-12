---
title: "What exactly is a server (defenition)"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by joramdam on 2008-02-12
This is possible the most stupid qestion on this forum but i don`t know exactly defenition. And of course i dont know how to set one up. I have understood so much that i will have use of one since i have 5 comuters at home. One for each family memder. I would also know howe to set up thin clients ? Hope somebody have patiens to answer such a newbee :)

---

### Post by jhenager on 2008-02-12
A server 'serves' files to client computers.
Your enthusiasm is commendable, but setting up a thin client/server network is something that you might nead to do some research on.
Networking your computers would be a more easily attainable goal.
If they are all Ubuntu, install NFS file sharing on each of them. If you are connecting to Windows machines, you will need SMB file sharing. Read up on Samba for more information on Linux--->Windows.
Have fun.

---

### Post by mike1821 on 2008-02-12
My friend,

Why do you want to setup a server. Are you sure you do not mean to setup a LAN (Local Area Network). 

Anyway, before proceeding in order to make your questions more specific why don't have a look om the following link. It will provide you all the basic idea about servers and their usability.

[http://en.wikipedia.org/wiki/Server_%28computing%29]("http://en.wikipedia.org/wiki/Server_%28computing%29")

---

### Post by nemilar on 2008-02-12
A server refers to any computer that responds to requests from clients.  There are *many* different types of servers; there are web servers, file servers, DNS servers, print servers, proxy servers, database servers, etc... The list goes on forever and ever.  In each of these cases, the server runs some sort of program that allows other computers to make requests to it; for example, a web server will be running an HTTP server software (for example, Apache) that allows other computers, via their web browser, to request a document over a network.

It would be helpful to know what kind of server you are interested in setting up.  A lot of homes have media fileservers, which are basically just computers with lots of hard drive space, and a program like Samba to allow people to access the files.

Most any linux distribution can be configured to act as some sort of server.  Ubuntu Desktop will work fine as a server OS, but the Ubuntu Server edition comes with more server-oriented packages, and doesn't have all the extras needed for the desktop (e.g, OpenOffice.org).

If you're looking to setup thin-clients, the easiest way of doing it is to install Ubuntu Desktop on your server machine, and have the other machines use SSH and X11 forwarding to run the programs remotely over the network.  They will be running on the server, but they will appear on the client.  You can get more information about SSH and X11 forwarding [from this SSH tutorial]("http://www.techthrob.com/tech/ssh101.php").

I hope this helps to answer your question!

---

### Post by joramdam on 2008-02-12
I have a local network, whith samba. 2 of the Pc is XP, and 3 ubuntu. Is a server defenition of a server that i have one PC whith a large disc, that i share files to the others computers. Then i already have a server, but i guess that is isnt that simple ? I share files and pictures from a home directory on my Ubuntu machine with the other.

---

### Post by AndyCooll on 2008-02-12
> **joramdam said:**
> I have a local network, whith samba. 2 of the Pc is XP, and 3 ubuntu. Is a server defenition of a server that i have one PC whith a large disc, that i share files to the others computers. Then i already have a server, but i guess that is isnt that simple ? I share files and pictures from a home directory on my Ubuntu machine with the other.

Yes, at it's most basic level that is a server, in this case the PC is operating as a file server. I used to have one machine that was always on and had a big shared hard-drive. I pointed all the other computers to it for all their music, documents etc.
Later I attached a printer to that box and shared that too ...then it was a simple file and print server. 

You need to decide exactly what you want, for as you may be gathering a server can be as simple or as complicated as you want to be. Remember too that there's always more than one way to achieve the same thing, so my advice is not to over-complicate your needs if they aren't necessary.

:cool:

---

### Post by joramdam on 2008-02-12
> **AndyCooll said:**
> Yes, at it's most basic level that is a server, in this case the PC is operating as a file server. I used to have one machine that was always on and had a big shared hard-drive. I pointed all the other computers to it for all their music, documents etc.
Later I attached a printer to that box and shared that too ...then it was a simple file and print server. 

You need to decide exactly what you want, for as you may be gathering a server can be as simple or as complicated as you want to be. Remember too that there's always more than one way to achieve the same thing, so my advice is not to over-complicate your needs if they aren't necessary.

:cool:

Nice answer, and of course you are surely right about not over complicate. But i also want to experimenting with the opportunity that exists :-). Espessialy thin clients. So if anyone have interesting opportunityes then shoot :-)

---

