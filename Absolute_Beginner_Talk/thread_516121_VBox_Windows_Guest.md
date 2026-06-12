---
title: "VBox Windows Guest"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-08-02
Is there an explanation of sharing files between a Unbuntu host and a XP guest that a 
human being could understand? I'm pretty computer literate, but the instructions for this thing are so vague. I can't tell if what I'm doing is even close to being right. All I know is that it is not working. In the linux host type( VBoxManage sharedfolder add "VM name" -name "sharename"
 -hostpath "C:\test") and then in the windows guest type(net use x: \\vboxsvr\sharename) This is all the instrutions they gave me in the innitek manual. Does the machine have to be powered off or on? where it says (-name) is that part of the command or am I supposed to replace it with the name of something? Same for (-hostpath) am I supposed to type "-hostpath" or "-/home/nolan/name-of-folder" I have the additions installed. The exact command I tried to use was " sudo VBoxManage sharedfolder add " Windows xp" -name Shared  
-hostpath C:\Shared " I didn't get any error messages, but when I typed "net use x: \\vboxsvr\Shared it told me there was an error retrieving the file. Can someone help me out with this please? Thanks.  :confused:

---

### Post by jackmc on 2007-08-02
Do it with the virtual machine off.

This page helped me a bit, mine is working now: [http://doc.gwos.org/index.php/VirtualBox#Sharing_your_hard_drive](http://doc.gwos.org/index.php/VirtualBox#Sharing_your_hard_drive)

First of all, make a folder (mine is called Shared, and it sits in /home/user_name/). My Machine name (set in VirtualBox) is WinXP

Using that example:
```

VBoxManage sharedfolder add "WinXP" -name Shared -hostpath "/home/user_name/Shared"

```

Then, power on the XP virtual machine, and go to run => cmd. Type

```

net use E: \\vboxsvr\Shared


```


After the two commands (one in ubuntu, one in XP), the shared folder shows up in My Computer.

Let me know if you have any issues.

---

### Post by jackmc on 2007-08-02
I just read your first post again - the shared folder will be on your ubuntu system, and Windows will link to it.

So instead of 
```

-hostpath C:\Shared

```
you'll need something like
```

-hostpath "/home/user_name/Shared"

```

- note the difference between the two strings (windows syntax in the first one, Linux in the second)

---

### Post by swoll1980 on 2007-08-02
Thanks alot I will try this and let you know

---

### Post by swoll1980 on 2007-08-02
Cool it worked.  thanks alot

---

### Post by climatewarrior on 2007-08-27
Hi! I followed all ofthe above directions but when I go to my windows XP guest and put the command in the coomand prompt I get the followng error. "System error 53 has ocurred. The  network path was not found" . I have already installed the Guest additions in my XP guest.Im running Ubuntu FeistyFawn 7.04. Thanks a lot bye!

---

### Post by schorsch on 2007-08-27
What is the output of 
```
VBoxManage list vms
```
and what exactly did you type to share the folder under Ubuntu?

---

### Post by yorgabr on 2007-08-27
Hi, schorsch!
I got the same trouble than climatewarrior. The output I had was:

[FONT="Fixedsys"]Name:            RuindowsXP
Guest OS:        Windows XP
UUID:            478c63f7-0bdc-43d6-f888-f3f7bb347017
Config file:     /home/yorga/.VirtualBox/Machines/RuindowsXP/RuindowsXP.xml
Memory size:     256MB
VRAM size:       16MB
Boot menu mode:  message and menu
ACPI:            on
IOAPIC:          off
Time offset:     0 ms
Hardw. virt.ext: off
State:           running (since 2007-08-27T14:55:16.824000000)
Floppy:          empty
Primary master:  /home/yorga/.VirtualBox/VDI/RuindowsXP.vdi (UUID: b5f9f9b7-c91e-4832-1f83-610b1c445111)
DVD:             Host drive /dev/hdc
NIC 1:           MAC: 080027AF3B17, Attachment: NAT, Trace: off (file: <NULL>)
NIC 2:           disabled
NIC 3:           disabled
NIC 4:           disabled
Audio:           enabled (Driver: ALSA)
Clipboard Mode:  Bidirectional
VRDP:            disabled
USB:             enabled

USB Device Filters:

<none>

Shared folders:

Name: 'recebidos', Host path: '/home/yorga/recebidos' (machine mapping)[/FONT]

Don't mind the name of my WinXP's virtual machine (it's a windows joke in my country).
Do you have any ideia what's preventing us to access the shared folders?

Thanks in advance!

---

### Post by schorsch on 2007-08-27
Hmm .... that seems to look alright. You should get it mounted when you use
```
net use Z: \\vboxsvr\recebidos
``` 
or via the Computer-Icon and then Extras - Map Network Drive. Note the Space between the colon and the first backslash!
BTW: Do you have the appropriate guest additions installed? After some updates from the VirtualBox package I had to uninstall them from the guest, reboot the guest and do a fresh install of the guest additions. Otherwise I had some trouble getting keyboard and mouse integration working. Perhaps this could be your problem, too?

---

### Post by sparttacus on 2007-08-27
I've fix the problem with:  /*/  Resolvi o problema com:

Add Shared Folder /*/ Adicionar pasta partilhada

System->Administration->Shared Folder  /*/  Sistema->Administracao->Pastas Partilhadas
Add /*/ Adicionar
Choose shared folder path /*/  Escolher Caminho da pasta pretendida
Shared through: Windows Network  /*/  Partilhar através de : Redes Windows(SMB)
Unchek Ready only /*/ Desactivar Apenas Leitura
OK
Close /*/ Fechar

In VirtualBox with virtual disk  powered off /*/ Em  VirtualBox com o disco desligado 
Settings->General->Advanced->Shared Clipboard->BiDirectional  /*/  Configuração->Geral->Avançado-<Area de Transferencia Compartilhada
Bi-direcional
OK

Start virtual disk session /*/ Iniciar Sessão do Windows no VirtualBox
Unmount CD/DVD-ROM /*/ Desactivar CD/DVD-ROM
Device->Install Guest Additions /*/ Dispositivos->Instalar Adicionais para Convidados
Follow Instructions /*/ Seguir instruções
Mount CD/DVD-ROM /*/ Reactivar CD/DVD-ROM
Start DOS session and insert /*/ Iniciar sessão em DOS e inserir

net use X: \\vboxsvr\sharedFolder  /*/  net use X: \\vboxsvr\nome_pasta_partilhada

Check My Computer for the new folder /*/ Verificar se aparece a pasta em Meu Computador

---

### Post by climatewarrior on 2007-08-27
This is the output of VBoxManage list vms

VirtualBox Command Line Management Interface Version 1.4.0
(C) 2005-2007 innotek GmbH
All rights reserved.

Name:            WinXP
Guest OS:        Windows XP
UUID:            4a0a93ac-f9b4-4cf0-4298-a3fe662bb908
Config file:     /home/gabo/.VirtualBox/Machines/WinXP/WinXP.xml
Memory size:     256MB
VRAM size:       32MB
Boot menu mode:  message and menu
ACPI:            on
IOAPIC:          off
Time offset:     0 ms
Hardw. virt.ext: off
State:           aborted (since 2007-08-27T18:51:52.000000000)
Floppy:          empty
Primary master:  /home/gabo/.VirtualBox/VDI/WinXp_elvirus.vdi (UUID: 47fafcfe-c046-4b27-27a3-1570c427fcd7)
DVD:             empty
NIC 1:           disabled
NIC 2:           MAC: 080027BC968B, Attachment: NAT, Trace: off (file: <NULL>)
NIC 3:           disabled
NIC 4:           disabled
Audio:           enabled (Driver: ALSA)
Clipboard Mode:  Bidirectional
VRDP:            disabled
USB:             disabled

USB Device Filters:

<none>

Shared folders:

Name: 'Shared', Host path: '/home/gabo/Shared' (machine mapping)

And this is are the instructions I followed

[QUOTE=jackmc;3124554]Do it with the virtual machine off.

This page helped me a bit, mine is working now: [http://doc.gwos.org/index.php/VirtualBox#Sharing_your_hard_drive](http://doc.gwos.org/index.php/VirtualBox#Sharing_your_hard_drive)

First of all, make a folder (mine is called Shared, and it sits in /home/user_name/). My Machine name (set in VirtualBox) is WinXP

Using that example:
```

VBoxManage sharedfolder add "WinXP" -name Shared -hostpath "/home/user_name/Shared"

```

Then, power on the XP virtual machine, and go to run => cmd. Type

```

net use E: \\vboxsvr\Shared


```

I also did this


I've fix the problem with: /*/ Resolvi o problema com:

Add Shared Folder /*/ Adicionar pasta partilhada

System->Administration->Shared Folder /*/ Sistema->Administracao->Pastas Partilhadas
Add /*/ Adicionar
Choose shared folder path /*/ Escolher Caminho da pasta pretendida
Shared through: Windows Network /*/ Partilhar através de : Redes Windows(SMB)
Unchek Ready only /*/ Desactivar Apenas Leitura
OK
Close /*/ Fechar

In VirtualBox with virtual disk powered off /*/ Em VirtualBox com o disco desligado
Settings->General->Advanced->Shared Clipboard->BiDirectional /*/ Configuração->Geral->Avançado-<Area de Transferencia Compartilhada
Bi-direcional
OK

Start virtual disk session /*/ Iniciar Sessão do Windows no VirtualBox
Unmount CD/DVD-ROM /*/ Desactivar CD/DVD-ROM
Device->Install Guest Additions /*/ Dispositivos->Instalar Adicionais para Convidados
Follow Instructions /*/ Seguir instruções
Mount CD/DVD-ROM /*/ Reactivar CD/DVD-ROM
Start DOS session and insert /*/ Iniciar sessão em DOS e inserir

net use X: \\vboxsvr\sharedFolder /*/ net use X: \\vboxsvr\nome_pasta_partilhada

Check My Computer for the new folder /*/ Verificar se aparece a pasta em Meu Computador

But im still getting the same error

---

