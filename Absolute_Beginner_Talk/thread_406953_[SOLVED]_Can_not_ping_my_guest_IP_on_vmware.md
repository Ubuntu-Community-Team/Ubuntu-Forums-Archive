---
title: "[SOLVED] Can not ping my guest IP on vmware"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by TheApe on 2007-04-11
Hi.

I have installed Windows XP Pro by vmware on my edgy dist.
It works great. I have shared folders from my linux Box at the Windows Guest. And also can access websistes, and access my apache at the host (Ubuntu).

The problem is that I have IIS instaled on the guest(windows) and wanted to access it from the my linux box... And I can`t even send a ping from the host to the guest... nothing is found.

The guest machine is configured to use NAT.
As I don't know too much about networking, I'm having these problems...


Can anyone help me?

Thank's!!!

---

### Post by Bachstelze on 2007-04-11
Are you sure you're using the correct IP ? You can find that out in windows with

```
ipconfig /all
```

in a command-line.

---

### Post by TheApe on 2007-04-11
Yeap, I'm shure...

```

C:\Documents and Settings\The Ape!!>ipconfig /all

Configuração de IP do Windows

        Nome do host . . . . . . . . . . . : apewindows
        Sufixo DNS primário. . . . . . . . :
        Tipo de nó . . . . . . . . . . . . : desconhecido
        Roteamento de IP ativado . . . . . : não
        Proxy WINS ativado . . . . . . . . : não
        Lista de pesquisa de sufixo DNS. . : localdomain

Adaptador Ethernet Conexão local:

        Sufixo DNS específico de conexão  . : localdomain
        Descrição . . . . . . . . . . . . . : VMware Accelerated AMD PCNet Adapt
er
        Endereço físico . . . . . . . . . . : 00-0C-29-5F-BE-97
        DHCP ativado. . . . . . . . . . . . : Sim
        Configuração automática ativada . . : Sim
        Endereço IP . . . . . . . . . . . . : 192.168.229.128
        Máscara de sub-rede . . . . . . . . : 255.255.255.0
        Gateway padrão. . . . . . . . . . . : 192.168.229.2
        Servidor DHCP . . . . . . . . . . . : 192.168.229.254
        Servidores DNS. . . . . . . . . . . : 192.168.229.2
        Concessão obtida. . . . . . . . . . : quarta-feira, 11 de abril de 2007
16:52:34
        Concessão expira. . . . . . . . . . : quarta-feira, 11 de abril de 2007
17:22:34

```

The IP is 192.168.229.128
But when I try to ping it on the ubuntu box..
```

theape@ape:~$ ping 192.168.229.128
PING 192.168.229.128 (192.168.229.128) 56(84) bytes of data.

```

And it stops...
Can it be some network policy? How can I found out?

Thanks for the reply.

---

### Post by TheApe on 2007-04-11
I started firestarter and now when I ping I get the following
[HTML]
PING 192.168.229.128 (192.168.229.128) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
[/HTML]

---

### Post by TheApe on 2007-04-11
The problem was the windows firewall active by defaul :-x

---

### Post by cajsdy on 2008-06-03
i have the same problem. my pc is runing winxp and have vmware workstation installed, then ubuntu 8.04 installed as virtual machine.
vmware workstation is in bridge mode.

ip address from ubuntu and win-xp are in the same subnet.

and ping between win-xp and guest ubuntu, no work at all.

sometimes, when play network setting from ubuntu, change static to dhcp and reboot ubuntu, may work or not.

then setup 2nd guest ubuntu, they can ping each other, but not to win-xp.

---

