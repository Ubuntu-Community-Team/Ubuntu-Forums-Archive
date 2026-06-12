---
title: "Avahi, CUPS, Ubuntu!"
date: 2012-08-29
forum: Apple Hardware Users
---

### Post by jdawgvh on 2012-08-29
I have Ubuntu Server running on a computer in the back room and a Mac as a client in the living room.  Everything is working fine between the two.  I can print, share files, everything that you would expect.  Recently, I tried to set up CUPS and Avahi so that I can print from my iPad.  To do this I have had to create another printer, which I called Airprint.  I can see Airprint from my Mac and even print to it.  This tells me that I'm not having a CUPS problem and that everything is configured correctly.  However, I cannot see Airprint from my iPad.  I believe I have Avahi configured wrong but I can't figure out where to go from here.  The .service file that I made is below:


<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
  <name>HP PhotoSmart Airprint</name>
  <service>
    <type>_ipp._tcp</type>
    <subtype>_universal._sub._ipp._tcp</subtype>
    <port>631</port>
    <txt-record>txtver=1</txt-record>
    <txt-record>qtotal=1</txt-record>
    <txt-record>rp=printers/Photosmart_C5100</txt-record>
    <txt-record>ty=HP PhotoSmart Airprint</txt-record>
    <txt-record>adminurl=ipp://198.168.1.246:631/printers/Photosmart_C5100</txt$
    <txt-record>note=HP PhotoSmart Airprint</txt-record>
    <txt-record>priority=0</txt-record>
    <txt-record>product=virtual Printer</txt-record>
    <txt-record>printer-state=3</txt-record>
    <txt-record>printer-type=0x801046</txt-record>
    <txt-record>Transparent=T</txt-record>
    <txt-record>Binary=T</txt-record>
    <txt-record>Fax=F</txt-record>
    <txt-record>Color=T</txt-record>
    <txt-record>Duplex=T</txt-record>
    <txt-record>Staple=F</txt-record>
    <txt-record>Copies=T</txt-record>
    <txt-record>Collate=F</txt-record>
    <txt-record>Punch=F</txt-record>
    <txt-record>Bind=F</txt-record>
    <txt-record>Sort=F</txt-record>
    <txt-record>Scan=F</txt-record>
    <txt-record>pdl=application/octet-stream,application/pdf,application/postsc$
    <txt-record>URF=W8,SRGB24,CP1,RS600</txt-record>
  </service>
</service-group>

---

### Post by jdawgvh on 2012-08-30
I could not get it to work with the auto generate avahi service script that keeps coming up if you google it.  I was, however, able to get it by manually editing the .service file based on this link after much googling

[http://http://www.finnie.org/2010/11/13/airprint-and-linux/]("http://http://www.finnie.org/2010/11/13/airprint-and-linux/")

---

