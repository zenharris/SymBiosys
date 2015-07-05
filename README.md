# SymBiosys
Symbiosys a 6502 operating system for IDE hard disks units.

Just testing out how this all works, quickly uploaded a disk opperating system I wrote on a 1978 SYM-1 microcomputer a few years ago. I do intend getting back to this and recoding it in a real assembler rather the the Sym's Resident Assembler Editor (which actually is a very good resident assembler environment once it's patched to use Symbiosys filesystem.

Get back to me if there is actually anyone interested in it, once recoded in any normal assembler it could easily be ported to any computer, it uses the VIA ports to bit bang the data to and from the IDE disk so no interface hardware other than wires from the VIA to the IDE.

Here is how my colleague mapped the interface out...

    Connecting a 6522 VIA to an ATA IDE bus
    ---------------------------------------


    Designed for a Synertek SYM-1, and its AA Expansion connector.


    PORTB0-7 maps to DATA0-7 on IDE
    PORTA0 = ADDR0
    PORTA1 = ADDR1
    PORTA2 = ADDR2
    PORTA3 = /RD
    PORTA4 = /WR
    PORTA5 = /CS0


    AA-pin         AAname*                  IDE
  

    1               GND                2,19,22,24,26,30,40,Power-
    3               A1                    15 (DATA1)
    7               B5                    37 (/CS0)
    8               B3                    25 (/RD)
    9               B1                    33 (ADDR1)
    10              A7                    3  (DATA7)
    11              A5                    7  (DATA5)
    12              A3                    11 (DATA3)
    13              RESET                 1  (jumpered)


    A               Vcc                 Power+
    C               A2                   13 (DATA2)
    D               A0                   17 (DATA0)
    J               B4                   23 (/WR)
    K               B2                   36 (ADDR2)
    L               B0                   35 (ADDR0)
    M               A6                   5  (DATA6)
    N               A4                   9  (DATA4)
                                         27 (IORDY) - tie low 10kR
                                         29 (DMACK) - tie high 1kR
                                         38 (/CS1)  - tie high 1kR
                                         39 (DASP)  - LED+180R to Vcc


*: as I discovered when debugging the code, what
the SYM1 calls PORT A on its AA expansion bus, is
actually PORTB to the 6522. The pinout is no different,
since I ended up changing the code to suit.

-- 
Chris Baird,, <cjb@brushtail.apana.org.au> Feb2010.
Corrected IORDY and DASP: 2010-Jul-31





I'll tidy this all up if anyone has interest.
