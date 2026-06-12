---
title: "Gràfica integrada d'ATI: requeriments del sistema ?"
date: 2010-01-18
forum: Catalan Team
---

### Post by sianeu on 2010-01-18
He canviat l'ordinador. La nova placa base es la asus M4A785TD-V EVO amb la gràfica integrada ATI 4200 amb 128Mb de memòria dedicada ddr3 1333 integrada a placa.

Ubuntu Karmic 9.10, no funciona en live-cd, però si funciona instal·lant el sistema. 

En la nova versió del driver propietari de ATI (Catlist 9.12) per Linux he vist que ja suporta la meva gràfica (En la versió 9.11 encara no hi era). 

Vull instal·lar-lo, però tinc dubtes pels requeriments minims del sistema que indiquen les instruccions:
Before attempting to install the ATI Proprietary Linux driver, the following software
must be installed:
   XOrg 6.8, 6.9, 7.0, 7.1, 7.2, 7.3 or 7.4
   Linux kernel 2.6 or above
   glibc version 2.2 or 2.3
   POSIX Shared Memory (/dev/shm) support is required for 3D applications
Els dos últims no els he trobat (faig servir el cercador del synaptic).

Tampoc ho tinc clar amb algunes "recomanacions":
System Recommendations
        For best performance and ease of use, ATI recommends the following:
            Kernel module build environment
            o Kernel source code include either the Kernel Source or Kernel Headers packages
            The RPM utility should be installed and configured correctly on your system, if you
            intend to install via RPM packages
        The following packages must be installed in order for the CatalystTM Linux driver to
        install and work properly:
            XFree86-Mesa-libGL --------------------> no trobat
            libstdc++ -----------------------------> instal·lat
            libgcc  -------------------------------> instal·lat libgcc1 (suposo que val)
            XFree86-libs --------------------------> no trobat
            fontconfig ----------------------------> instal·lat
            freetype ------------------------------> no trobat
            zlib ----------------------------------> instal·lat zlib1g, no instal·lats: zlib-bin, zlibc, zlib-gst
            gcc -----------------------------------> instal·lat

Potser es que varia el nom del paquet, o potser els tinc de buscar per un altre banda. Necessito un cop de ma.


Salut

PD; El meu sistema es el Karmic 64bits. La pàgina d'on he baixat el driver i el manual [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.5.3.1&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.5.3.1&lang=English")

---

