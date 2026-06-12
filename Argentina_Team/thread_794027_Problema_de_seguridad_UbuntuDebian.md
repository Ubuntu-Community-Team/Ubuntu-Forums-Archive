---
title: "Problema de seguridad Ubuntu/Debian"
date: 2008-05-14
forum: Argentina Team
---

### Post by faktorqm on 2008-05-14
Hola, me llego un mail de launchpad advirtiendo sobre una vulnerabilidad en la generacion de las claves. Acá pongo los link, y la traduccion abajo (la lista de paquetes es la misma en ambos):

[http://www.ubuntu.com/usn/usn-612-1](http://www.ubuntu.com/usn/usn-612-1)
[http://www.ubuntu.com/usn/usn-612-2](http://www.ubuntu.com/usn/usn-612-2)
[http://www.ubuntu.com/usn/usn-612-3](http://www.ubuntu.com/usn/usn-612-3)

=========================================================== 
Ubuntu Security Notice USN-612-1               May 13, 2008
openssl vulnerability
CVE-2008-0166
===========================================================

A weakness has been discovered in the random number generator used
by OpenSSL on Debian and Ubuntu systems.  As a result of this
weakness, certain encryption keys are much more common than they
should be, such that an attacker could guess the key through a
brute-force attack given minimal knowledge of the system.  This
particularly affects the use of encryption keys in OpenSSH, OpenVPN
and SSL certificates.

This vulnerability only affects operating systems which (like
Ubuntu) are based on Debian.  However, other systems can be
indirectly affected if weak keys are imported into them.

We consider this an extremely serious vulnerability, and urge all
users to act immediately to secure their systems. (CVE-2008-0166)

This advisory also applies to the corresponding versions of
Kubuntu, Edubuntu, and Xubuntu.

== Who is affected ==

Systems which are running any of the following releases:

 * Ubuntu 7.04 (Feisty)
 * Ubuntu 7.10 (Gutsy)
 * Ubuntu 8.04 LTS (Hardy)
 * Ubuntu "Intrepid Ibex" (development): libssl <= 0.9.8g-8
 * Debian 4.0 (etch) (see corresponding Debian security advisory)

and have openssh-server installed or have been used to create an
OpenSSH key or X.509 (SSL) certificate.

All OpenSSH and X.509 keys generated on such systems must be
considered untrustworthy, regardless of the system on which they
are used, even after the update has been applied.

This includes the automatically generated host keys used by OpenSSH,
which are the basis for its server spoofing and man-in-the-middle
protection.

Blacklists have been created for certain known-vulnerable keys and
certificates. Please see the following advisories for more
information:

  [http://www.ubuntu.com/usn/usn-612-2](http://www.ubuntu.com/usn/usn-612-2) (OpenSSH)
  [http://www.ubuntu.com/usn/usn-612-3](http://www.ubuntu.com/usn/usn-612-3) (OpenVPN)


The problem can be corrected by upgrading your system to the
following package versions:


[COLOR="Blue"]Una vulnerabilidad fue descubierta en el generador de números aleatorios utilizado por OpenSSL en sistemas Debian y Ubuntu. Como resultado de esta vulnerabilidad, algunas llaves encriptadas son mucho mas comunes de lo que deberian, de modo que un atacante podria averiguar la clave a través de un ataque de fuerza bruta aún con un conocimiento mínimo sobre el sistema. Esto afecta particularmente al uso de estas llaves en OpenSSH, OpenVPN y certificados SSL.

Esta vulnerabilidad solo afecta a sistemas operativos que (como ubuntu) estan basados en Debian. Sin embargo, otros sistemas pueden ser indirectamente afectados si las claves "débiles" fueron importadas a ellos.

Consideramos que esta es una vulnerabilidad muy grave, y nos urge que todos los usuarios deben actuar de inmediato para que sus sistemas sean seguros.(CVE-2008-0166)

Este aviso también se aplica a las correspondientes versiones de Kubuntu, Edubuntu, y Xubuntu.

=== ¿Quien está afectado? ===

Aquellos sistemas que están corriendo cualquiera de las siguientes versiones:

 * Ubuntu 7.04 (Feisty)
 * Ubuntu 7.10 (Gutsy)
 * Ubuntu 8.04 LTS (Hardy)
 * Ubuntu "Intrepid Ibex" (development): libssl <= 0.9.8g-8
 * Debian 4.0 (etch) (Ver correspondiente aviso de seguridad en Debian)

y tienen instalado openssh-server o éste se ha utilizado en llaves OpenSSH o certificados X.509 (SSL).

Todas las llaves OpenSSH y X.509 generadas en estos sitemas deben ser consideradas NO-SEGURAS, independientemente del sistema en que 
se utilizaron, e incluso después de la actualización si se ha aplicado.

Esto incluye las llaves de host generadas automáticamente utilizadas por  OpenSSH, que son la base de un servidor de "spoofing" y para la proteccion "hombre-en-el-medio".

Unas listas negras fueron creadas para algunas llaves y certificados con vulnerabilidad conocida. Por favor vea los siguientes avisos para más información:

  [http://www.ubuntu.com/usn/usn-612-2](http://www.ubuntu.com/usn/usn-612-2) (OpenSSH)
  [http://www.ubuntu.com/usn/usn-612-3](http://www.ubuntu.com/usn/usn-612-3) (OpenVPN)

El problema puede ser solucionado actualizando su sistema a las versiones de los siguientes paquetes:[/COLOR]

Ubuntu 7.04:
  libssl0.9.8                     0.9.8c-4ubuntu0.3

Ubuntu 7.10:
  libssl0.9.8                     0.9.8e-5ubuntu3.2

Ubuntu 8.04 LTS:
  libssl0.9.8                     0.9.8g-4ubuntu3.1

Updated packages for Ubuntu 7.04:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8c-4ubuntu0.3.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8c-4ubuntu0.3.diff.gz)
      Size/MD5:    55960 f1528622672403589e0d3aac4091e3b7
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8c-4ubuntu0.3.dsc](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8c-4ubuntu0.3.dsc)
      Size/MD5:      899 24ce07dd1372b34976caa4e703b48254
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8c.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8c.orig.tar.gz)
      Size/MD5:  3313857 78454bec556bcb4c45129428a766c886

  amd64 architecture (Athlon64, Opteron, EM64T Xeon):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8c-4ubuntu0.3_amd64.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8c-4ubuntu0.3_amd64.udeb)
      Size/MD5:   604324 c67285c8c9831d7d688930bf3403070e
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8c-4ubuntu0.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8c-4ubuntu0.3_amd64.deb)
      Size/MD5:  2186920 ebfec7f633c445ae170b06acb039175c
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8c-4ubuntu0.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8c-4ubuntu0.3_amd64.deb)
      Size/MD5:  1645270 3c37713de4ad97e6eb675f9f8a9b3ddd
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8c-4ubuntu0.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8c-4ubuntu0.3_amd64.deb)
      Size/MD5:   918170 c282b7478265a81019e771a382ec99cd
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8c-4ubuntu0.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8c-4ubuntu0.3_amd64.deb)
      Size/MD5:  1006504 a199460e3209b03f454afa205abbd979

  i386 architecture (x86 compatible Intel/AMD):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8c-4ubuntu0.3_i386.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8c-4ubuntu0.3_i386.udeb)
      Size/MD5:   569520 9441a49f438e5c0c77c70f9c50b3acee
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8c-4ubuntu0.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8c-4ubuntu0.3_i386.deb)
      Size/MD5:  2068628 152dc5bd9d6edb669be2a4d88fdc9126
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8c-4ubuntu0.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8c-4ubuntu0.3_i386.deb)
      Size/MD5:  5499922 4e07a86c1f4930411fffc25cb330f683
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8c-4ubuntu0.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8c-4ubuntu0.3_i386.deb)
      Size/MD5:  2809850 dd17842504c08b5a09e7ec15dee20f8b
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8c-4ubuntu0.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8c-4ubuntu0.3_i386.deb)
      Size/MD5:  1001316 f823d1e7c4ea63e976fd129a2bfe5fed

  powerpc architecture (Apple Macintosh G3/G4/G5):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8c-4ubuntu0.3_powerpc.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8c-4ubuntu0.3_powerpc.udeb)
      Size/MD5:   617086 d8158b21c17afbd21460dfee4a001194
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8c-4ubuntu0.3_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8c-4ubuntu0.3_powerpc.deb)
      Size/MD5:  2217842 90507ac4c5dce8110853c8e71c366004
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8c-4ubuntu0.3_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8c-4ubuntu0.3_powerpc.deb)
      Size/MD5:  1705352 d2ac68501fc799a5033824d204ac0175
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8c-4ubuntu0.3_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8c-4ubuntu0.3_powerpc.deb)
      Size/MD5:   939544 1e6af8a9427957566434357f346096d9
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8c-4ubuntu0.3_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8c-4ubuntu0.3_powerpc.deb)
      Size/MD5:  1014948 b6c5a7b2c97df56cff30d1797490705f

  sparc architecture (Sun SPARC/UltraSPARC):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8c-4ubuntu0.3_sparc.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8c-4ubuntu0.3_sparc.udeb)
      Size/MD5:   563014 dd59635ac83a1c84fe59b7d8ab9b2992
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8c-4ubuntu0.3_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8c-4ubuntu0.3_sparc.deb)
      Size/MD5:  2111944 e647e97fbb98c2ce48c8fce8517c92d0
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8c-4ubuntu0.3_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8c-4ubuntu0.3_sparc.deb)
      Size/MD5:  4053968 b26c15bf44dc732832251f8cb1002b15
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8c-4ubuntu0.3_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8c-4ubuntu0.3_sparc.deb)
      Size/MD5:  2205868 0b767362c79d60942cbe473deecad932
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8c-4ubuntu0.3_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8c-4ubuntu0.3_sparc.deb)
      Size/MD5:  1016770 f6940cc99ec5b841d4a54b9cb38af203

Updated packages for Ubuntu 7.10:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2.diff.gz)
      Size/MD5:    58261 712fb9938545440a484c383c8a6ac7f7
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2.dsc](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2.dsc)
      Size/MD5:      950 b47e6ac103c4bcc8d969faf994c8a887
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e.orig.tar.gz)
      Size/MD5:  3341665 3a7ff24f6ea5cd711984722ad654b927

  amd64 architecture (Athlon64, Opteron, EM64T Xeon):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8e-5ubuntu3.2_amd64.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8e-5ubuntu3.2_amd64.udeb)
      Size/MD5:   608582 4e66d471698d449a31e206d91972ac77
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8e-5ubuntu3.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8e-5ubuntu3.2_amd64.deb)
      Size/MD5:  2065236 eb0982f5fdc2988b4a1adc3535a92cec
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8e-5ubuntu3.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8e-5ubuntu3.2_amd64.deb)
      Size/MD5:  1644030 45659a7dadef747fb828a11bf00b6466
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8e-5ubuntu3.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8e-5ubuntu3.2_amd64.deb)
      Size/MD5:   928852 cbbc47991050e043a259065d6e63d3f1
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2_amd64.deb)
      Size/MD5:   877820 d5254e3c81c503be7ec8d908985ca27d

  i386 architecture (x86 compatible Intel/AMD):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8e-5ubuntu3.2_i386.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8e-5ubuntu3.2_i386.udeb)
      Size/MD5:   571794 33ed14cad215235c7f3e3959417e618a
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8e-5ubuntu3.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8e-5ubuntu3.2_i386.deb)
      Size/MD5:  1943124 63d90e3f64c213a4033caa78adbb3481
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8e-5ubuntu3.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8e-5ubuntu3.2_i386.deb)
      Size/MD5:  5520470 9ffd3c29c28109498b530d5062d2537a
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8e-5ubuntu3.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8e-5ubuntu3.2_i386.deb)
      Size/MD5:  2825460 8265f8e385f34559d74ccca533c02a7a
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2_i386.deb)
      Size/MD5:   872078 09113bb86f530a81ab0a9ea3cff847cb

  lpia architecture (Low Power Intel Architecture):

    [http://ports.ubuntu.com/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8e-5ubuntu3.2_lpia.udeb](http://ports.ubuntu.com/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8e-5ubuntu3.2_lpia.udeb)
      Size/MD5:   537248 b14a7de8a4d2dc6c0636bcea065a25d9
    [http://ports.ubuntu.com/pool/main/o/openssl/libssl-dev_0.9.8e-5ubuntu3.2_lpia.deb](http://ports.ubuntu.com/pool/main/o/openssl/libssl-dev_0.9.8e-5ubuntu3.2_lpia.deb)
      Size/MD5:  1922036 22e02a08b6042d2037ed82a05cbe5968
    [http://ports.ubuntu.com/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8e-5ubuntu3.2_lpia.deb](http://ports.ubuntu.com/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8e-5ubuntu3.2_lpia.deb)
      Size/MD5:  1557052 34ac9b97e2297d773f00ec0cf9e9ed28
    [http://ports.ubuntu.com/pool/main/o/openssl/libssl0.9.8_0.9.8e-5ubuntu3.2_lpia.deb](http://ports.ubuntu.com/pool/main/o/openssl/libssl0.9.8_0.9.8e-5ubuntu3.2_lpia.deb)
      Size/MD5:   836566 2b357cdf056d2bdfc3d00eef8d758f12
    [http://ports.ubuntu.com/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2_lpia.deb](http://ports.ubuntu.com/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2_lpia.deb)
      Size/MD5:   876586 96f16cd47d93e94dbffb7bd7deb93284

  powerpc architecture (Apple Macintosh G3/G4/G5):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8e-5ubuntu3.2_powerpc.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8e-5ubuntu3.2_powerpc.udeb)
      Size/MD5:   618002 6949577d5d0dff62f1a87843556fce47
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8e-5ubuntu3.2_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8e-5ubuntu3.2_powerpc.deb)
      Size/MD5:  2093118 d1118570fb10780532a114316870024f
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8e-5ubuntu3.2_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8e-5ubuntu3.2_powerpc.deb)
      Size/MD5:  1704998 06a83dfb0b7463b2e0c48c957ad3e94f
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8e-5ubuntu3.2_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8e-5ubuntu3.2_powerpc.deb)
      Size/MD5:   945758 be53ff03675982367b0615701c0c9012
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2_powerpc.deb)
      Size/MD5:   886184 dd98564311d595033534eb7c6f396718

  sparc architecture (Sun SPARC/UltraSPARC):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8e-5ubuntu3.2_sparc.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8e-5ubuntu3.2_sparc.udeb)
      Size/MD5:   565188 0ca872b583b61d0d15a872e83378782d
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8e-5ubuntu3.2_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8e-5ubuntu3.2_sparc.deb)
      Size/MD5:  1987272 9334f39b64dbc1765bf0b8bc1c5c0113
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8e-5ubuntu3.2_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8e-5ubuntu3.2_sparc.deb)
      Size/MD5:  4049724 69782f2dbd642b303551e128c1552aa3
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8e-5ubuntu3.2_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8e-5ubuntu3.2_sparc.deb)
      Size/MD5:  2220894 8ae7f5b7585bd9e4f1392f76fd3bcc71
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2_sparc.deb)
      Size/MD5:   887244 d6320a2c885ce0eae7dcc27f569a0963

Updated packages for Ubuntu 8.04 LTS:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8g-4ubuntu3.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8g-4ubuntu3.1.diff.gz)
      Size/MD5:    52455 febf7cb03f479b0a3adcae06eb02203b
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8g-4ubuntu3.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8g-4ubuntu3.1.dsc)
      Size/MD5:      912 0a14742d144c1389dcbc52f47ba3f7c8
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8g.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8g.orig.tar.gz)
      Size/MD5:  3354792 acf70a16359bf3658bdfb74bda1c4419

  Architecture independent packages:

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl-doc_0.9.8g-4ubuntu3.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl-doc_0.9.8g-4ubuntu3.1_all.deb)
      Size/MD5:   628518 80043d691d2bf742c6874b237ed659c6

  amd64 architecture (Athlon64, Opteron, EM64T Xeon):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8g-4ubuntu3.1_amd64.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8g-4ubuntu3.1_amd64.udeb)
      Size/MD5:   603886 e1c9837aaa00f00c030be0948f2666f8
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8g-4ubuntu3.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8g-4ubuntu3.1_amd64.deb)
      Size/MD5:  2064554 4fd6b7dba2501356363e4c88876e7016
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8g-4ubuntu3.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8g-4ubuntu3.1_amd64.deb)
      Size/MD5:  1603796 877c7dc84a0a442a71322466aaf0191d
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.1_amd64.deb)
      Size/MD5:   931158 936aeaeb9c0acfa73ce04362ef20f235
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8g-4ubuntu3.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8g-4ubuntu3.1_amd64.deb)
      Size/MD5:   390622 5ece5cbc091a8955ec7dc47b6494c42e

  i386 architecture (x86 compatible Intel/AMD):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8g-4ubuntu3.1_i386.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8g-4ubuntu3.1_i386.udeb)
      Size/MD5:   564666 e428bac008437846a9411a34f7e46e8b
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8g-4ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8g-4ubuntu3.1_i386.deb)
      Size/MD5:  1941644 b6edc3acd3a90c42baaf8819fd9f3256
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8g-4ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8g-4ubuntu3.1_i386.deb)
      Size/MD5:  5340876 a1a31e52f2b6ce5b00a2e550e1c9a9f7
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.1_i386.deb)
      Size/MD5:  2828048 4ef2062996432b694e1a06eaf61818aa
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8g-4ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8g-4ubuntu3.1_i386.deb)
      Size/MD5:   385434 f29998409853097ebe60730295c81e7b

  lpia architecture (Low Power Intel Architecture):

    [http://ports.ubuntu.com/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8g-4ubuntu3.1_lpia.udeb](http://ports.ubuntu.com/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8g-4ubuntu3.1_lpia.udeb)
      Size/MD5:   535450 2a6c4f477589124df101fdf508bf170d
    [http://ports.ubuntu.com/pool/main/o/openssl/libssl-dev_0.9.8g-4ubuntu3.1_lpia.deb](http://ports.ubuntu.com/pool/main/o/openssl/libssl-dev_0.9.8g-4ubuntu3.1_lpia.deb)
      Size/MD5:  1922630 bfe69691602e76835d998443fecf6bf5
    [http://ports.ubuntu.com/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8g-4ubuntu3.1_lpia.deb](http://ports.ubuntu.com/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8g-4ubuntu3.1_lpia.deb)
      Size/MD5:  1512332 c90b961b61a02198b87b503d1f7f01ce
    [http://ports.ubuntu.com/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.1_lpia.deb](http://ports.ubuntu.com/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.1_lpia.deb)
      Size/MD5:   842712 69b457eef0ae45f342e01bd13c83be2d
    [http://ports.ubuntu.com/pool/main/o/openssl/openssl_0.9.8g-4ubuntu3.1_lpia.deb](http://ports.ubuntu.com/pool/main/o/openssl/openssl_0.9.8g-4ubuntu3.1_lpia.deb)
      Size/MD5:   390028 41001b11916fd7d522580060ad298d16

  powerpc architecture (Apple Macintosh G3/G4/G5):

    [http://ports.ubuntu.com/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8g-4ubuntu3.1_powerpc.udeb](http://ports.ubuntu.com/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8g-4ubuntu3.1_powerpc.udeb)
      Size/MD5:   610282 8c4ff25d4e5695eba1e0ea6e0fba22b1
    [http://ports.ubuntu.com/pool/main/o/openssl/libssl-dev_0.9.8g-4ubuntu3.1_powerpc.deb](http://ports.ubuntu.com/pool/main/o/openssl/libssl-dev_0.9.8g-4ubuntu3.1_powerpc.deb)
      Size/MD5:  2077924 35d088aee3c0ed62b9a18d861fca08b9
    [http://ports.ubuntu.com/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8g-4ubuntu3.1_powerpc.deb](http://ports.ubuntu.com/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8g-4ubuntu3.1_powerpc.deb)
      Size/MD5:  1639052 85d14e648caaaf6fab7acae470d7e1b2
    [http://ports.ubuntu.com/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.1_powerpc.deb](http://ports.ubuntu.com/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.1_powerpc.deb)
      Size/MD5:   944496 3f561d17a732a995c61a99bb58be0348
    [http://ports.ubuntu.com/pool/main/o/openssl/openssl_0.9.8g-4ubuntu3.1_powerpc.deb](http://ports.ubuntu.com/pool/main/o/openssl/openssl_0.9.8g-4ubuntu3.1_powerpc.deb)
      Size/MD5:   399190 b7cdcf3e46bb497fc0d9f0ebd1e670d2

  sparc architecture (Sun SPARC/UltraSPARC):

    [http://ports.ubuntu.com/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8g-4ubuntu3.1_sparc.udeb](http://ports.ubuntu.com/pool/main/o/openssl/libcrypto0.9.8-udeb_0.9.8g-4ubuntu3.1_sparc.udeb)
      Size/MD5:   559662 1e68facc899f2a355ffc5ba9d74873fb
    [http://ports.ubuntu.com/pool/main/o/openssl/libssl-dev_0.9.8g-4ubuntu3.1_sparc.deb](http://ports.ubuntu.com/pool/main/o/openssl/libssl-dev_0.9.8g-4ubuntu3.1_sparc.deb)
      Size/MD5:  1984618 3d1892e144d9e360091fca9970bac61a
    [http://ports.ubuntu.com/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8g-4ubuntu3.1_sparc.deb](http://ports.ubuntu.com/pool/main/o/openssl/libssl0.9.8-dbg_0.9.8g-4ubuntu3.1_sparc.deb)
      Size/MD5:  3873424 769e051711a442675147042e60fa6e3b
    [http://ports.ubuntu.com/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.1_sparc.deb](http://ports.ubuntu.com/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.1_sparc.deb)
      Size/MD5:  2241226 c21c1ea84171285a241ed7ec31fb2d2d
    [http://ports.ubuntu.com/pool/main/o/openssl/openssl_0.9.8g-4ubuntu3.1_sparc.deb](http://ports.ubuntu.com/pool/main/o/openssl/openssl_0.9.8g-4ubuntu3.1_sparc.deb)
      Size/MD5:   397810 31bccc57af7b0dc1dd6d9005bbdedb2c


Ahora adjunto la continuacion del aviso:

=========================================================== 
Ubuntu Security Notice USN-612-2               May 13, 2008
openssh vulnerability
CVE-2008-0166, [http://www.ubuntu.com/usn/usn-612-1](http://www.ubuntu.com/usn/usn-612-1)
===========================================================

A weakness has been discovered in the random number generator used
by OpenSSL on Debian and Ubuntu systems.  As a result of this
weakness, certain encryption keys are much more common than they
should be, such that an attacker could guess the key through a
brute-force attack given minimal knowledge of the system.  This
particularly affects the use of encryption keys in OpenSSH.

This vulnerability only affects operating systems which (like
Ubuntu) are based on Debian.  However, other systems can be
indirectly affected if weak keys are imported into them.

We consider this an extremely serious vulnerability, and urge all
users to act immediately to secure their systems.

The following Ubuntu releases are affected:

Ubuntu 7.04
Ubuntu 7.10
Ubuntu 8.04 LTS

This advisory also applies to the corresponding versions of
Kubuntu, Edubuntu, and Xubuntu.


Updating your system:

1. Install the security updates

   Ubuntu 7.04:
     openssh-client                  1:4.3p2-8ubuntu1.3
     openssh-server                  1:4.3p2-8ubuntu1.3

   Ubuntu 7.10:
     openssh-client                  1:4.6p1-5ubuntu0.3
     openssh-server                  1:4.6p1-5ubuntu0.3

   Ubuntu 8.04 LTS:
     openssh-client                  1:4.7p1-8ubuntu1.1
     openssh-server                  1:4.7p1-8ubuntu1.1

   Once the update is applied, weak user keys will be automatically
   rejected where possible (though they cannot be detected in all
   cases). If you are using such keys for user authentication,
   they will immediately stop working and will need to be replaced
   (see step 3).

   OpenSSH host keys can be automatically regenerated when the
   OpenSSH security update is applied. The update will prompt for
   confirmation before taking this step.

2. Update OpenSSH known_hosts files

   The regeneration of host keys will cause a warning to be displayed
   when connecting to the system using SSH until the host key is
   updated in the known_hosts file. The warning will look like this:

   @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
   @    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
   @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
   IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
   Someone could be eavesdropping on you right now (man-in-the-middle
   attack)! It is also possible that the RSA host key has just been
   changed.

   In this case, the host key has simply been changed, and you
   should update the relevant known_hosts file as indicated in the
   error message.

3. Check all OpenSSH user keys

   The safest course of action is to regenerate all OpenSSH user
   keys, except where it can be established to a high degree of
   certainty that the key was generated on an unaffected system.

   Check whether your key is affected by running the ssh-vulnkey
   tool, included in the security update. By default, ssh-vulnkey
   will check the standard location for user keys (~/.ssh/id_rsa,
   ~/.ssh/id_dsa and ~/.ssh/identity), your authorized_keys file
   (~/.ssh/authorized_keys and ~/.ssh/authorized_keys2), and the
   system's host keys (/etc/ssh/ssh_host_dsa_key and
   /etc/ssh/ssh_host_rsa_key).

   To check all your own keys, assuming they are in the standard
   locations (~/.ssh/id_rsa, ~/.ssh/id_dsa, or ~/.ssh/identity):

   $ ssh-vulnkey

   To check all keys on your system:

   $ sudo ssh-vulnkey -a

   To check a key in a non-standard location:

   $ ssh-vulnkey /path/to/key

   If ssh-vulnkey says "COMPROMISED", the key is vulnerable and
   should be replaced.

   If ssh-vulnkey says "Unknown (no blacklist information)",
   then it has no information about whether that key is affected
   because the key is of a type for which no blacklist is
   available.

   If in doubt, destroy the key and generate a new one.

4. Regenerate any affected user keys

   OpenSSH keys used for user authentication must be manually
   regenerated, including those which may have since been
   transferred to a different system after being generated.

   New keys can be generated using ssh-keygen, e.g.:

   $ ssh-keygen
   Generating public/private rsa key pair.
   Enter file in which to save the key (/home/user/.ssh/id_rsa):
   Enter passphrase (empty for no passphrase):
   Enter same passphrase again:
   Your identification has been saved in /home/user/.ssh/id_rsa.
   Your public key has been saved in /home/user/.ssh/id_rsa.pub.
   The key fingerprint is:
   00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00 user@host

5. Update authorized_keys files (if necessary)

   Once the user keys have been regenerated, the relevant public
   keys must be propagated to any authorized_keys files on
   remote systems.  Be sure to delete the affected key.


[COLOR="Blue"]Una vulnerabilidad fue descubierta en el generador de números aleatorios utilizado por OpenSSL en sistemas Debian y Ubuntu. Como resultado de esta vulnerabilidad, algunas llaves encriptadas son mucho mas comunes de lo que deberian, de modo que un atacante podria averiguar la clave a través de un ataque de fuerza bruta aún con un conocimiento mínimo sobre el sistema. Esto afecta particularmente al uso de estas llaves en OpenSSH.

Esta vulnerabilidad solo afecta a sistemas operativos que (como ubuntu) estan basados en Debian. Sin embargo, otros sistemas pueden ser indirectamente afectados si las claves "débiles" fueron importadas a ellos.

Consideramos que esta es una vulnerabilidad extremadamente grave, y nos urge que todos los usuarios deben actuar de inmediato para que sus sistemas sean seguros.

Las siguientes versiones de ubuntu están afectadas:

* Ubuntu 7.04
* Ubuntu 7.10
* Ubuntu 8.04 LTS

Este aviso también se aplica a las correspondientes versiones de Kubuntu, Edubuntu, y Xubuntu.

Actualizando su sistema:

1. Instale las actualizaciones de seguridad:

   Ubuntu 7.04:
     openssh-client                  1:4.3p2-8ubuntu1.3
     openssh-server                  1:4.3p2-8ubuntu1.3

   Ubuntu 7.10:
     openssh-client                  1:4.6p1-5ubuntu0.3
     openssh-server                  1:4.6p1-5ubuntu0.3

   Ubuntu 8.04 LTS:
     openssh-client                  1:4.7p1-8ubuntu1.1
     openssh-server                  1:4.7p1-8ubuntu1.1

Una vez que la actualizacion es aplicada, las claves débiles de usuario automaticamente serán rechazadas en la medida de lo posible (NO es posible detectar claves debiles en todos los casos). Si usted esta utilizando dichas claves para autentificacion de usuario, inmediatamente debe descartar su uso y reemplazarlas. (ver paso 3)

Las llaves OpenSSH pueden ser regeneradas automaticamente cuando el parche de seguridad de OpenSSH sea aplicado. La actualizacion le pedirá una confirmación antes de realizar este paso.

2.  La regeneración de claves de host pueden causar un aviso que se mostrará cuando se conecte al sistema usando SSH hasta que la clave de host sea actualizada en el archivo known_hosts. El cartel de aviso se ve algo parecido a esto:

   @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
   @ CUIDADO: LA IDENTIFICACION DE HOST REMOTO HA CAMBIADO!! @
   @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
   ES POSIBLE QUE ALGUIEN ESTE HACIENDO COSAS DESAGRADABLES!
   Alguien lo podria estar espiando ahora mismo (ataque de
   hombre-en-el-medio!) También es posible que la clave RSA haya cambiado.


En este caso, la clave de host simplemente ha sido cambiada, y tu deberias actualizar el archivo known_hosts pertinente como es indicado en el mensaje de error.

3. Chequear todas las claves de usuario OpenSSH

La manera mas segura de hacer esto es regenerar todas las claves de usuario OpenSSH, salvo cuando pueda demostrarse a un alto grado de 
certeza de que la clave se generó en un sistema no afectado.

Chequee si su clave se ve afectada corriendo la herramienta ssh-vulnkey, incluida en la actualizacion de seguridad. Por defecto, ssh-vulnkey revisará la ubicación estandard de las llaves de usuario (~/.ssh/id_rsa,
~/.ssh/id_dsa y ~/.ssh/identity), tu archivo authorized_keys (~/.ssh/authorized_keys y ~/.ssh/authorized_keys2) y las llaves de sistema (/etc/ssh/ssh_host_dsa_key y /etc/ssh/ssh_host_rsa_key).

Para comprobar todas tus llaves, y asumiendo que estan en las ubicaciones estadares, (~/.ssh/id_rsa, ~/.ssh/id_dsa, or ~/.ssh/identity) hacer:

```
$ ssh-vulnkey
```

Para comprobar todas las llaves del sistema:

```
$ sudo ssh-vulnkey -a
```

PAra comprobar una llave en una ubicación no estandard:

```
$ ssh-vulnkey /path/to/key
```

Si ssh-vulnkey dice "COMPROMISED",(comprometido) la clave es vulnerable y deberias reemplazarla.

Si ssh-vulnkey dice "Unknown (no blacklist information)" (desconocido (no hay informacion en la lista negra)) entonces no hay informacion acerca de 
si la llave esta afectada o no por que no es del tipo que esta en la lista negra. Si estas en la duda, elimine la llave y genere una nueva.

  
4. Regenerar cualquier llave de usuario afectada

Las llaves OpenSSH utilizadas para la autenticación de usuarios deben ser regeneradas manualmente, incluidas los que puedieron haber sido trasladadas a un sistema diferente después de haber sido generadas.

Las nuevas claves se pueden generar utilizando ssh-keygen, por ejemplo:

```

$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/user/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/user/.ssh/id_rsa.
Your public key has been saved in /home/user/.ssh/id_rsa.pub.
The key fingerprint is:
00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00 user@host
$
```

5. Actualizar los archivos authorized_keys (si es necesario)

Una vez que las claves de usuario se hayan regenerado, las claves públicas relevantes deben ser propagadas con cualquier archivo authorized_keys en sistemas remotos. Asegúrese de eliminar las claves afectadas.[/COLOR]


Updated packages for Ubuntu 7.04:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.3p2-8ubuntu1.3.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.3p2-8ubuntu1.3.diff.gz)
      Size/MD5:   275518 a8b32463625d995f31710932955f155e
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.3p2-8ubuntu1.3.dsc](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.3p2-8ubuntu1.3.dsc)
      Size/MD5:     1074 2ba8f9d6823e429a87a16d1069b8bcb0
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.3p2.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.3p2.orig.tar.gz)
      Size/MD5:   920186 239fc801443acaffd4c1f111948ee69c

  Architecture independent packages:

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh_4.3p2-8ubuntu1.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh_4.3p2-8ubuntu1.3_all.deb)
      Size/MD5:     1086 ec4e33a5b72165a213aba1dc5c6e1e48
    [http://security.ubuntu.com/ubuntu/pool/universe/o/openssh/ssh-krb5_4.3p2-8ubuntu1.3_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/o/openssh/ssh-krb5_4.3p2-8ubuntu1.3_all.deb)
      Size/MD5:    93414 1273931c48c521f82a32c83d3c2c7f30

  amd64 architecture (Athlon64, Opteron, EM64T Xeon):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.3p2-8ubuntu1.3_amd64.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.3p2-8ubuntu1.3_amd64.udeb)
      Size/MD5:   173116 a63a1aad1a6d703701353b1a2f3aa3f1
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.3p2-8ubuntu1.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.3p2-8ubuntu1.3_amd64.deb)
      Size/MD5:   739306 6ebf534da00e63d36ff8d25d133c5f87
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.3p2-8ubuntu1.3_amd64.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.3p2-8ubuntu1.3_amd64.udeb)
      Size/MD5:   185954 165979d39473eed093bd332294611892
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.3p2-8ubuntu1.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.3p2-8ubuntu1.3_amd64.deb)
      Size/MD5:   255690 5f273f1e6da9f6f572da970e7ba1680a
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.3p2-8ubuntu1.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.3p2-8ubuntu1.3_amd64.deb)
      Size/MD5:   101788 18268a8507e35a673ba0b88d7c8f905b

  i386 architecture (x86 compatible Intel/AMD):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.3p2-8ubuntu1.3_i386.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.3p2-8ubuntu1.3_i386.udeb)
      Size/MD5:   156814 338d87e0ed113fabb31bf8985c41044d
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.3p2-8ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.3p2-8ubuntu1.3_i386.deb)
      Size/MD5:   701434 47f4f9e32772a27f390b7bf598ca692c
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.3p2-8ubuntu1.3_i386.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.3p2-8ubuntu1.3_i386.udeb)
      Size/MD5:   165480 bb943025f0bfb39c0f080aa0c6a90507
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.3p2-8ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.3p2-8ubuntu1.3_i386.deb)
      Size/MD5:   238154 cc0df0b6336c02dda018dd381e096150
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.3p2-8ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.3p2-8ubuntu1.3_i386.deb)
      Size/MD5:   101494 d84b4274b86d65878b41e33db957cbec

  powerpc architecture (Apple Macintosh G3/G4/G5):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.3p2-8ubuntu1.3_powerpc.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.3p2-8ubuntu1.3_powerpc.udeb)
      Size/MD5:   178908 fb39252bf076dca363b34058f6c6280a
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.3p2-8ubuntu1.3_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.3p2-8ubuntu1.3_powerpc.deb)
      Size/MD5:   767364 cbe597ba0193d39d115a432404471939
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.3p2-8ubuntu1.3_powerpc.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.3p2-8ubuntu1.3_powerpc.udeb)
      Size/MD5:   184132 ebc03fba90aa40ba7e86c2bd90b4b43b
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.3p2-8ubuntu1.3_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.3p2-8ubuntu1.3_powerpc.deb)
      Size/MD5:   259734 1feeb20163fb303b41a85bbd9775abe5
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.3p2-8ubuntu1.3_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.3p2-8ubuntu1.3_powerpc.deb)
      Size/MD5:   104262 f781bfd69b35508129c0ce71eb0cf395

  sparc architecture (Sun SPARC/UltraSPARC):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.3p2-8ubuntu1.3_sparc.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.3p2-8ubuntu1.3_sparc.udeb)
      Size/MD5:   164240 2796884a4e9c6a0c4d228e3a2d829df4
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.3p2-8ubuntu1.3_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.3p2-8ubuntu1.3_sparc.deb)
      Size/MD5:   751366 43659331cc6f294e7657d96311db221a
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.3p2-8ubuntu1.3_sparc.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.3p2-8ubuntu1.3_sparc.udeb)
      Size/MD5:   172576 f3bebc7681083a2a7dd4a91fd1ee5237
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.3p2-8ubuntu1.3_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.3p2-8ubuntu1.3_sparc.deb)
      Size/MD5:   263460 913bae4437faf91b7c4b95257ca9fe46
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.3p2-8ubuntu1.3_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.3p2-8ubuntu1.3_sparc.deb)
      Size/MD5:   101742 cf3e2aa66bfe30c2981a28063d7fa639

Updated packages for Ubuntu 7.10:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.6p1-5ubuntu0.3.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.6p1-5ubuntu0.3.diff.gz)
      Size/MD5:   195240 fe9c399991e5e754a0837760ff9d4100
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.6p1-5ubuntu0.3.dsc](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.6p1-5ubuntu0.3.dsc)
      Size/MD5:     1169 fc9b6d0a04345973f1b88ca9aa8e6a32
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.6p1.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.6p1.orig.tar.gz)
      Size/MD5:   946439 cee58cd226138191561fa2d484e18f49

  Architecture independent packages:

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh_4.6p1-5ubuntu0.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh_4.6p1-5ubuntu0.3_all.deb)
      Size/MD5:     1092 56a70a7d56d8d7722f33d60b6cd17a71
    [http://security.ubuntu.com/ubuntu/pool/universe/o/openssh/ssh-krb5_4.6p1-5ubuntu0.3_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/o/openssh/ssh-krb5_4.6p1-5ubuntu0.3_all.deb)
      Size/MD5:    80578 9d3e66bfbbac576c23ee4bf9827ed545

  amd64 architecture (Athlon64, Opteron, EM64T Xeon):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.6p1-5ubuntu0.3_amd64.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.6p1-5ubuntu0.3_amd64.udeb)
      Size/MD5:   176410 3167e74074387dc17c98c38e1b98fd3c
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.3_amd64.deb)
      Size/MD5:   746302 cc544fd8322a83dab8eb5f342eaca137
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.6p1-5ubuntu0.3_amd64.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.6p1-5ubuntu0.3_amd64.udeb)
      Size/MD5:   193380 7defa55f2553fd71e391d33f392acd0e
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.6p1-5ubuntu0.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.6p1-5ubuntu0.3_amd64.deb)
      Size/MD5:   268750 6d5c5179be8f291956b30cc36d4ee091
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.3_amd64.deb)
      Size/MD5:    88726 97c9adfa3a82f9ed54286f68b41ef966

  i386 architecture (x86 compatible Intel/AMD):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.6p1-5ubuntu0.3_i386.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.6p1-5ubuntu0.3_i386.udeb)
      Size/MD5:   158796 e4d1cc24210b4a3327cafd41a559cd6b
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.3_i386.deb)
      Size/MD5:   705630 c18488f740b38d1a57aef8806924de8a
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.6p1-5ubuntu0.3_i386.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.6p1-5ubuntu0.3_i386.udeb)
      Size/MD5:   171690 af3ba10602d74429b54e256fbc982187
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.6p1-5ubuntu0.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.6p1-5ubuntu0.3_i386.deb)
      Size/MD5:   249760 ab084428f73b76c5b4db1e648a222aa4
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.3_i386.deb)
      Size/MD5:    88384 b051562fb7973c1dd92e6a8bb6b22854

  lpia architecture (Low Power Intel Architecture):

    [http://ports.ubuntu.com/pool/main/o/openssh/openssh-client-udeb_4.6p1-5ubuntu0.3_lpia.udeb](http://ports.ubuntu.com/pool/main/o/openssh/openssh-client-udeb_4.6p1-5ubuntu0.3_lpia.udeb)
      Size/MD5:   158876 1bffbee3eed3146e3feaa2c802537699
    [http://ports.ubuntu.com/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.3_lpia.deb](http://ports.ubuntu.com/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.3_lpia.deb)
      Size/MD5:   676546 d22322abdfa831ea95bf42540aafecd6
    [http://ports.ubuntu.com/pool/main/o/openssh/openssh-server-udeb_4.6p1-5ubuntu0.3_lpia.udeb](http://ports.ubuntu.com/pool/main/o/openssh/openssh-server-udeb_4.6p1-5ubuntu0.3_lpia.udeb)
      Size/MD5:   171284 e59f9929f2fcc857d44131d76500c210
    [http://ports.ubuntu.com/pool/main/o/openssh/openssh-server_4.6p1-5ubuntu0.3_lpia.deb](http://ports.ubuntu.com/pool/main/o/openssh/openssh-server_4.6p1-5ubuntu0.3_lpia.deb)
      Size/MD5:   243102 8b5d5ff193b90fff85cec8aee1b8cfbc
    [http://ports.ubuntu.com/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.3_lpia.deb](http://ports.ubuntu.com/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.3_lpia.deb)
      Size/MD5:    88414 52ed9be1d8933742c15c14f7cfee11dd

  powerpc architecture (Apple Macintosh G3/G4/G5):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.6p1-5ubuntu0.3_powerpc.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.6p1-5ubuntu0.3_powerpc.udeb)
      Size/MD5:   180856 20b436d113f09e07b9c53301f87a551a
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.3_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.3_powerpc.deb)
      Size/MD5:   773758 b7c0f8ac855ea770bbdf58284f25546e
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.6p1-5ubuntu0.3_powerpc.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.6p1-5ubuntu0.3_powerpc.udeb)
      Size/MD5:   190236 23961af7588d4a886d818248c8c7fa15
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.6p1-5ubuntu0.3_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.6p1-5ubuntu0.3_powerpc.deb)
      Size/MD5:   271988 e8bdf4fa9838997c0bd62446c59b38dd
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.3_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.3_powerpc.deb)
      Size/MD5:    91094 b8756a6901f7a0337c36c7cc76d4991c

  sparc architecture (Sun SPARC/UltraSPARC):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.6p1-5ubuntu0.3_sparc.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.6p1-5ubuntu0.3_sparc.udeb)
      Size/MD5:   166884 139dc1f86d43517a46ec3915b61125e1
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.3_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.3_sparc.deb)
      Size/MD5:   758584 5b8cba657c6e53342e119d26dc9b7c61
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.6p1-5ubuntu0.3_sparc.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.6p1-5ubuntu0.3_sparc.udeb)
      Size/MD5:   179096 0bccc7c29ed50a559b02e52087ae4ed2
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.6p1-5ubuntu0.3_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.6p1-5ubuntu0.3_sparc.deb)
      Size/MD5:   276534 4a4ce6ed933a3c03f632e1b3a7f34e18
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.3_sparc.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.3_sparc.deb)
      Size/MD5:    88696 a0158a6b98ff0531c1893caf4b01ebdf

Updated packages for Ubuntu 8.04 LTS:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.7p1-8ubuntu1.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.7p1-8ubuntu1.1.diff.gz)
      Size/MD5:   208492 b33a4acef918d79a2d0450011fd9db88
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.7p1-8ubuntu1.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.7p1-8ubuntu1.1.dsc)
      Size/MD5:     1135 19ea91251f9de2f6dfa6d936a8e4025b
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.7p1.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh_4.7p1.orig.tar.gz)
      Size/MD5:  1009361 bea83d2e0f9ac7b3d4393d693e68b5c1

  Architecture independent packages:

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh_4.7p1-8ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh_4.7p1-8ubuntu1.1_all.deb)
      Size/MD5:     1084 ec75a470768ccd89eb6c107244d25843
    [http://security.ubuntu.com/ubuntu/pool/universe/o/openssh/ssh-krb5_4.7p1-8ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/o/openssh/ssh-krb5_4.7p1-8ubuntu1.1_all.deb)
      Size/MD5:    88740 16ff461b87a6baa09ececbc9697af6ed

  amd64 architecture (Athlon64, Opteron, EM64T Xeon):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.7p1-8ubuntu1.1_amd64.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.7p1-8ubuntu1.1_amd64.udeb)
      Size/MD5:   179266 1e32b7dbecf022791c6ab251a8d86117
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.7p1-8ubuntu1.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.7p1-8ubuntu1.1_amd64.deb)
      Size/MD5:   760430 1e6d3bdf27d9657c9eefeee0b5b6dd6f
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.7p1-8ubuntu1.1_amd64.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.7p1-8ubuntu1.1_amd64.udeb)
      Size/MD5:   195488 267a48a1b35ab7855894e7785224dc57
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.7p1-8ubuntu1.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.7p1-8ubuntu1.1_amd64.deb)
      Size/MD5:   272820 81b2527ce22794c0281484fdc1de86c1
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.7p1-8ubuntu1.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.7p1-8ubuntu1.1_amd64.deb)
      Size/MD5:    96646 14c612c40c4c414eccf11db95e404a67

  i386 architecture (x86 compatible Intel/AMD):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.7p1-8ubuntu1.1_i386.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client-udeb_4.7p1-8ubuntu1.1_i386.udeb)
      Size/MD5:   161826 a1081ddbc0d082133770cd8412774b01
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.7p1-8ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.7p1-8ubuntu1.1_i386.deb)
      Size/MD5:   720024 3bcf4ba3a85f4464e13bb7d0b1574548
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.7p1-8ubuntu1.1_i386.udeb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server-udeb_4.7p1-8ubuntu1.1_i386.udeb)
      Size/MD5:   174336 77153868defe66100d1ab2d4949aed80
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.7p1-8ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_4.7p1-8ubuntu1.1_i386.deb)
      Size/MD5:   254010 3ad390fe06cf32b5aced76ce944839ce
    [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.7p1-8ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.7p1-8ubuntu1.1_i386.deb)
      Size/MD5:    96282 505e7cd7b1b5e8f9e8c2401e61b84f78

  lpia architecture (Low Power Intel Architecture):

    [http://ports.ubuntu.com/pool/main/o/openssh/openssh-client-udeb_4.7p1-8ubuntu1.1_lpia.udeb](http://ports.ubuntu.com/pool/main/o/openssh/openssh-client-udeb_4.7p1-8ubuntu1.1_lpia.udeb)
      Size/MD5:   161638 f14258648dc6485d895621c360caf87a
    [http://ports.ubuntu.com/pool/main/o/openssh/openssh-client_4.7p1-8ubuntu1.1_lpia.deb](http://ports.ubuntu.com/pool/main/o/openssh/openssh-client_4.7p1-8ubuntu1.1_lpia.deb)
      Size/MD5:   713374 176cceb970938c3d4e664c9ecdcafe8f
    [http://ports.ubuntu.com/pool/main/o/openssh/openssh-server-udeb_4.7p1-8ubuntu1.1_lpia.udeb](http://ports.ubuntu.com/pool/main/o/openssh/openssh-server-udeb_4.7p1-8ubuntu1.1_lpia.udeb)
      Size/MD5:   174208 12e49f067940cc99cdd91037e415d57f
    [http://ports.ubuntu.com/pool/main/o/openssh/openssh-server_4.7p1-8ubuntu1.1_lpia.deb](http://ports.ubuntu.com/pool/main/o/openssh/openssh-server_4.7p1-8ubuntu1.1_lpia.deb)
      Size/MD5:   252862 4ff6983dfc76b1d9893c3eeac0da19b9
    [http://ports.ubuntu.com/pool/main/o/openssh/ssh-askpass-gnome_4.7p1-8ubuntu1.1_lpia.deb](http://ports.ubuntu.com/pool/main/o/openssh/ssh-askpass-gnome_4.7p1-8ubuntu1.1_lpia.deb)
      Size/MD5:    96290 19ba2f10620c2565b41306d5392d86b9

  powerpc architecture (Apple Macintosh G3/G4/G5):

    [http://ports.ubuntu.com/pool/main/o/openssh/openssh-client-udeb_4.7p1-8ubuntu1.1_powerpc.udeb](http://ports.ubuntu.com/pool/main/o/openssh/openssh-client-udeb_4.7p1-8ubuntu1.1_powerpc.udeb)
      Size/MD5:   185708 46e102bc1076e9b1efe01430e0424a14
    [http://ports.ubuntu.com/pool/main/o/openssh/openssh-client_4.7p1-8ubuntu1.1_powerpc.deb](http://ports.ubuntu.com/pool/main/o/openssh/openssh-client_4.7p1-8ubuntu1.1_powerpc.deb)
      Size/MD5:   797090 4dc43223deedb0d4115a09d06cf352c3
    [http://ports.ubuntu.com/pool/main/o/openssh/openssh-server-udeb_4.7p1-8ubuntu1.1_powerpc.udeb](http://ports.ubuntu.com/pool/main/o/openssh/openssh-server-udeb_4.7p1-8ubuntu1.1_powerpc.udeb)
      Size/MD5:   194522 d7384655c312fcba85cd31efe4b4e0de
    [http://ports.ubuntu.com/pool/main/o/openssh/openssh-server_4.7p1-8ubuntu1.1_powerpc.deb](http://ports.ubuntu.com/pool/main/o/openssh/openssh-server_4.7p1-8ubuntu1.1_powerpc.deb)
      Size/MD5:   279012 afc9f70d7df19d39ce61b7ee18e7040a
    [http://ports.ubuntu.com/pool/main/o/openssh/ssh-askpass-gnome_4.7p1-8ubuntu1.1_powerpc.deb](http://ports.ubuntu.com/pool/main/o/openssh/ssh-askpass-gnome_4.7p1-8ubuntu1.1_powerpc.deb)
      Size/MD5:    99064 f593634bf8755c8ef348457cd9478be9

  sparc architecture (Sun SPARC/UltraSPARC):

    [http://ports.ubuntu.com/pool/main/o/openssh/openssh-client-udeb_4.7p1-8ubuntu1.1_sparc.udeb](http://ports.ubuntu.com/pool/main/o/openssh/openssh-client-udeb_4.7p1-8ubuntu1.1_sparc.udeb)
      Size/MD5:   169976 450612c9a43ddf84d2dd97e2422a3b22
    [http://ports.ubuntu.com/pool/main/o/openssh/openssh-client_4.7p1-8ubuntu1.1_sparc.deb](http://ports.ubuntu.com/pool/main/o/openssh/openssh-client_4.7p1-8ubuntu1.1_sparc.deb)
      Size/MD5:   723070 f51ac3477b3a6554277ebb26ef6c2496
    [http://ports.ubuntu.com/pool/main/o/openssh/openssh-server-udeb_4.7p1-8ubuntu1.1_sparc.udeb](http://ports.ubuntu.com/pool/main/o/openssh/openssh-server-udeb_4.7p1-8ubuntu1.1_sparc.udeb)
      Size/MD5:   181564 55312d8015761b003ca8abf6c6c0e6b5
    [http://ports.ubuntu.com/pool/main/o/openssh/openssh-server_4.7p1-8ubuntu1.1_sparc.deb](http://ports.ubuntu.com/pool/main/o/openssh/openssh-server_4.7p1-8ubuntu1.1_sparc.deb)
      Size/MD5:   258334 c67396a961ca1baf4adb3dc60974fe8e
    [http://ports.ubuntu.com/pool/main/o/openssh/ssh-askpass-gnome_4.7p1-8ubuntu1.1_sparc.deb](http://ports.ubuntu.com/pool/main/o/openssh/ssh-askpass-gnome_4.7p1-8ubuntu1.1_sparc.deb)
      Size/MD5:    96500 2ee312a10a8ff807ce94f8ecf0587588


Ahora, la continuacion y ultima parte:

=========================================================== 
Ubuntu Security Notice USN-612-3               May 13, 2008
openvpn vulnerability
CVE-2008-0166, [http://www.ubuntu.com/usn/usn-612-1](http://www.ubuntu.com/usn/usn-612-1)
===========================================================

A weakness has been discovered in the random number generator used
by OpenSSL on Debian and Ubuntu systems.  As a result of this
weakness, certain encryption keys are much more common than they
should be, such that an attacker could guess the key through a
brute-force attack given minimal knowledge of the system.  This
particularly affects the use of shared encryption keys and SSL/TLS
certificates in OpenVPN.

This vulnerability only affects operating systems which (like
Ubuntu) are based on Debian.  However, other systems can be
indirectly affected if weak keys are imported into them.

We consider this an extremely serious vulnerability, and urge all
users to act immediately to secure their systems.

The following Ubuntu releases are affected: 

Ubuntu 7.04
Ubuntu 7.10
Ubuntu 8.04 LTS

This advisory also applies to the corresponding versions of
Kubuntu, Edubuntu, and Xubuntu.

The problem can be corrected by upgrading your system to the
following package versions:

Ubuntu 7.04:
  openvpn                         2.0.9-5ubuntu0.1

Ubuntu 7.10:
  openvpn                         2.0.9-8ubuntu0.1

Ubuntu 8.04 LTS:
  openvpn                         2.1~rc7-1ubuntu3.1


Details follow:

   Once the update is applied, weak shared encryption keys and
   SSL/TLS certificates will be rejected where possible (though
   they cannot be detected in all cases). If you are using such
   keys or certificates, OpenVPN will not start and the keys or
   certificates will need to be regenerated.

   The safest course of action is to regenerate all OpenVPN
   certificates and key files, except where it can be established
   to a high degree of certainty that the certificate or shared key
   was generated on an unaffected system.

   Once the update is applied, you can check for weak OpenVPN shared
   secret keys with the openvpn-vulnkey command.

   $ openvpn-vulnkey /path/to/key

   OpenVPN shared keys can be regenerated using the openvpn command.

   $ openvpn --genkey --secret 

   Additionally, you can check for weak SSL/TLS certificates by
   installing openssl-blacklist via your package manager, and using
   the openssl-vulnkey command.

   $ openssl-vulnkey /path/to/key

   Please note that openssl-vulnkey only checks RSA private keys
   with 1024 and 2048 bit lengths. If in doubt, destroy the
   certificate and/or key and generate a new one. Please consult the
   OpenVPN documentation when recreating SSL/TLS certificates.

   Also, if certificates have been generated for use on other systems,
   they must be found and replaced as well.


[COLOR="Blue"]Una vulnerabilidad fue descubierta en el generador de números aleatorios utilizado por OpenSSL en sistemas Debian y Ubuntu. Como resultado de esta vulnerabilidad, algunas llaves encriptadas son mucho mas comunes de lo que deberian, de modo que un atacante podria averiguar la clave a través de un ataque de fuerza bruta aún con un conocimiento mínimo sobre el sistema. Esto afecta particularmente al uso de llaves compartidas y certificados SSL/TLS en OpenVPN.

Esta vulnerabilidad solo afecta a sistemas operativos que (como ubuntu) estan basados en Debian. Sin embargo, otros sistemas pueden ser indirectamente afectados si las claves "débiles" fueron importadas a ellos.

Consideramos que esta es una vulnerabilidad extremadamente grave, y nos urge que todos los usuarios deben actuar de inmediato para que sus sistemas sean seguros.

Las siguientes versiones de ubuntu están afectadas:

* Ubuntu 7.04
* Ubuntu 7.10
* Ubuntu 8.04 LTS

Este aviso también se aplica a las correspondientes versiones de Kubuntu, Edubuntu, y Xubuntu.

El problema puede ser corregido actualizando los paquetes de sus sistema a las siguientes versiones:

Ubuntu 7.04:
  openvpn                         2.0.9-5ubuntu0.1

Ubuntu 7.10:
  openvpn                         2.0.9-8ubuntu0.1

Ubuntu 8.04 LTS:
  openvpn                         2.1~rc7-1ubuntu3.1

Detalles:

Una vez que la actualizacion es aplicada, las claves débiles de usuario automaticamente serán rechazadas en la medida de lo posible (NO es posible detectar claves debiles en todos los casos). Si usted esta utilizando claves o certificados, OpenVPN no iniciará y las claves o los certificados deberán ser regenerados.

El camino más seguro para salvar el problema es regenerar todas los certificados OpenVPN y los archivos llave, salvo cuando pueda demostrarse a un alto grado de certeza de que la clave se generó en un sistema no afectado.

Una vez que la actualizacion es aplicada, vos podés comprobar las claves secretas compartidas OpenVPN con el comando openvpn-vulnkey.

```
$ openvpn-vulnkey /path/to/key
```

Las claves compartidas OpenVPN pueden ser regeneradas utilizando el comando openvpn.

```
$ openvpn --genkey --secret
``` 

Además, vos podés comprobar los certificados SSL/TLS "débiles" instalando openssl-blacklist a través de tu administrador de paquetes, y luego utilizar el comando openssl-vulnkey

```
$ openssl-vulnkey /path/to/key
```

NOTAR que openssl-vulnkey solo chequea las llaves privadas RSA con una longitud de 1024 o 2048 bits. Si tenes dudas elimina el certificado y/o la llave y genera todo de vuelta. Consulte la documentación de OpenVPN cuando regenere los certificados SSL/TLS.

También, si los certificados han sido generados para utilizar en otros sistemas, estos deben ser encontrados y reemplazados cuando corresponda.
[/COLOR]


Updated packages for Ubuntu 7.04:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-5ubuntu0.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-5ubuntu0.1.diff.gz)
      Size/MD5:    60747 8a64cba41a38497fe25ef36afa3297a4
    [http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-5ubuntu0.1.dsc](http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-5ubuntu0.1.dsc)
      Size/MD5:      641 18586d5869fb67929f2330dba3730498
    [http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9.orig.tar.gz)
      Size/MD5:   669076 60745008b90b7dbe25fe8337c550fec6

  amd64 architecture (Athlon64, Opteron, EM64T Xeon):

    [http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-5ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-5ubuntu0.1_amd64.deb)
      Size/MD5:   356162 cff07c3dbbc6b56a4932d91b6049499e

  i386 architecture (x86 compatible Intel/AMD):

    [http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-5ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-5ubuntu0.1_i386.deb)
      Size/MD5:   337190 2ece431df11236714da50fc28a63f238

  powerpc architecture (Apple Macintosh G3/G4/G5):

    [http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-5ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-5ubuntu0.1_powerpc.deb)
      Size/MD5:   357868 b9877bc7840768f0002a8e8016e8401a

  sparc architecture (Sun SPARC/UltraSPARC):

    [http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-5ubuntu0.1_sparc.deb](http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-5ubuntu0.1_sparc.deb)
      Size/MD5:   335978 8ff9625fb34f49e64cfb8811bb787b3a

Updated packages for Ubuntu 7.10:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-8ubuntu0.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-8ubuntu0.1.diff.gz)
      Size/MD5:    64195 02287a5ee333a17db50cb43c9d902433
    [http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-8ubuntu0.1.dsc](http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-8ubuntu0.1.dsc)
      Size/MD5:      642 d2a6e3308144f656dbfd35526e944187
    [http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9.orig.tar.gz)
      Size/MD5:   669076 60745008b90b7dbe25fe8337c550fec6

  amd64 architecture (Athlon64, Opteron, EM64T Xeon):

    [http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-8ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-8ubuntu0.1_amd64.deb)
      Size/MD5:   361852 19adb72a25cb5a4803bbc7e4b787d08f

  i386 architecture (x86 compatible Intel/AMD):

    [http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-8ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-8ubuntu0.1_i386.deb)
      Size/MD5:   341626 0fe67ae7eee3fd15900e78243dbec409

  lpia architecture (Low Power Intel Architecture):

    [http://ports.ubuntu.com/pool/universe/o/openvpn/openvpn_2.0.9-8ubuntu0.1_lpia.deb](http://ports.ubuntu.com/pool/universe/o/openvpn/openvpn_2.0.9-8ubuntu0.1_lpia.deb)
      Size/MD5:   343206 51f7d5738b58ce8315fee4cf9a6855cf

  powerpc architecture (Apple Macintosh G3/G4/G5):

    [http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-8ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-8ubuntu0.1_powerpc.deb)
      Size/MD5:   363094 1b3067714e8cc68a494715d39b2f0b63

  sparc architecture (Sun SPARC/UltraSPARC):

    [http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-8ubuntu0.1_sparc.deb](http://security.ubuntu.com/ubuntu/pool/universe/o/openvpn/openvpn_2.0.9-8ubuntu0.1_sparc.deb)
      Size/MD5:   341314 6bf8aa1066a79f4f0a17750fa0376238

Updated packages for Ubuntu 8.04 LTS:

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/o/openvpn/openvpn_2.1~rc7-1ubuntu3.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/o/openvpn/openvpn_2.1~rc7-1ubuntu3.1.diff.gz)
      Size/MD5:    35191 c3c32ea1efcc83a0deb61f3adcfc1609
    [http://security.ubuntu.com/ubuntu/pool/main/o/openvpn/openvpn_2.1~rc7-1ubuntu3.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/o/openvpn/openvpn_2.1~rc7-1ubuntu3.1.dsc)
      Size/MD5:      646 35a1021ae123a548cd57aeba15385b9e
    [http://security.ubuntu.com/ubuntu/pool/main/o/openvpn/openvpn_2.1~rc7.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/o/openvpn/openvpn_2.1~rc7.orig.tar.gz)
      Size/MD5:   786288 dac8b5104b5eb105ba82b2525d371d58

  amd64 architecture (Athlon64, Opteron, EM64T Xeon):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openvpn/openvpn_2.1~rc7-1ubuntu3.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openvpn/openvpn_2.1~rc7-1ubuntu3.1_amd64.deb)
      Size/MD5:   390828 537d1c0fba3fd2ea1853f2cd59df8c39

  i386 architecture (x86 compatible Intel/AMD):

    [http://security.ubuntu.com/ubuntu/pool/main/o/openvpn/openvpn_2.1~rc7-1ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openvpn/openvpn_2.1~rc7-1ubuntu3.1_i386.deb)
      Size/MD5:   372070 402b12a2ba4b1aa706e6160fe4c4c18b

  lpia architecture (Low Power Intel Architecture):

    [http://ports.ubuntu.com/pool/main/o/openvpn/openvpn_2.1~rc7-1ubuntu3.1_lpia.deb](http://ports.ubuntu.com/pool/main/o/openvpn/openvpn_2.1~rc7-1ubuntu3.1_lpia.deb)
      Size/MD5:   371074 acf51c0ab94e0f8a052d8e16de01c918

  powerpc architecture (Apple Macintosh G3/G4/G5):

    [http://ports.ubuntu.com/pool/main/o/openvpn/openvpn_2.1~rc7-1ubuntu3.1_powerpc.deb](http://ports.ubuntu.com/pool/main/o/openvpn/openvpn_2.1~rc7-1ubuntu3.1_powerpc.deb)
      Size/MD5:   391320 5315f5eda07a544d11c4ae415414f756

  sparc architecture (Sun SPARC/UltraSPARC):

    [http://ports.ubuntu.com/pool/main/o/openvpn/openvpn_2.1~rc7-1ubuntu3.1_sparc.deb](http://ports.ubuntu.com/pool/main/o/openvpn/openvpn_2.1~rc7-1ubuntu3.1_sparc.deb)
      Size/MD5:   368786 96633aff8986fe2fedcbed30bb3090dd


Esto lo traduje yo, asi que no aseguro que este excento de errores, ni de errores de redaccion XDXD, ni de errores gramaticales. Faltan acentos, etcetc. 
Bueno espero que les haya servido si no se enteraron. Salu2!!:KS

---

