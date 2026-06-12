---
title: "[SOLVED] Getting Xubuntu online via DSL"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by tbrminsanity on 2006-08-01
I am running Xubuntu on a Compaq Armada 1750 and I have a StarTech UE1205 Network Adapter card that I want to use to get my laptop online.  I have found the drivers to download (though I need to pay for them :-x) and I was wondering is there an easier way to get the card running on Xubuntu (except re-installing Xubuntu)?  I have tried to do pppoeconf so far and it tried manconf but both couldn't see the card.  The card does have power and is rx a signal so I know the card is good.

---

### Post by tbrminsanity on 2006-08-03
I have fixed this problem with the following:
----------------------------------------------
             Linux PCMCIA/CardBus LAN cards installation Guide(Rev:0.01)
                      Date: 1999/05/13
CONTENTS
 1. Introductions
 2. Installing PCMCIA Card Services
    2.1 Configuration for LAN cards
 3. Copyright

1. Introductions
  This document briefly describes how to use the PCMCIA/CardBus LAN cards
  in a Linux operating system. To make use of the PCMCIA/CardBus LAN cards,
  you need to install the PCMCIA Card Services which responds to card
  insertion and removal events, loading and unloading drivers on demand.

  Chapter two discusses the installation of the PCMCIA Card Services as
  well as the configuration of LAN cards.

2. Installing the PCMCIA Card Services
  Card Serives for Linux is written by David Hinds
  <dhinds@hyper.stanford.edu>. It is now a part of many of the Linux
  distributions, like RedHat and Slackware. You need to install it into
  your Linux system for use of the PCMCIA or "PC Card". The source version
  is available at <hyper.stanford.edu> in the "/pub/pcmcia" dirctory,as
  "pcmcia-cs-x.tar.gz". Replace "x" with the version number of the latest
  package.

  To install the PCMCIA Card Services, you need to install a full kernel
  source and do the following shell commands:

        #tar zxvf pcmcia-cs-x.tar.gz
        #cd pcmcia-cs-x
        #./Configure
        #make all
        #make install

  Generally, you don't need to change any default selections when you run
  "./Configure" to configure the compiled environment. But if you want to
  use Card Bus adapter, enable the (CardBus) option.

2.1 Configuration for LAN cards
  For LAN card users, you need to use editor to edit the file
  "/etc/pcmcia/network.opts" to assign IP address, netmask, gateway IP,
  nameservers,broadcast address, and etc. after the Card Services
  installation. A part of the file "network.opts" is as listed which is
  mandatory setup for the TCP/IP of your Linux machine:

        #File: /etc/pcmcia/network.opts
        #
        #
        #
        #Host's IP address, netmask, network address, broadcast address
        IPADDR="1.2.3.4"
        NETMASK="255.255.255.0"
        NETWORK="1.2.3.0"
        BROADCAST="1.2.3.255"
        #Gateway address for static routing
        GATEWAY="1.2.3.254"
        #Things to add to /etc/resolv.conf for this interface
        DOMAIN="your.domain"
        SEARCH=""
        DNS_1=""
        DNS_2=""
        DNS_3=""
        #
        #

  Remember to reboot your Linux machine for the Card Services after
  installation.

  Now you should have the PCMCIA Card Services installed correctly.
  If the Card Service is not installed properly, please see the
  "PCMCIA-HOWTO" for the details in the root directory of the Card
  Services source code to resolve installation and configuraton
  problems.

3. Copyrights
  This document can be freely used and redistributed without any prior
  permission.
-------------------------------------------------

---

