1.라우터 인터페이스 구조 (2811 + NM-2FE2W)

모듈을 추가하면 2811 라우터에 포트가 잡힘

Fa0/0, Fa0/1 → 기본 내장 FastEthernet

Fa1/0, Fa1/1 → NM-2FE2W 모듈에서 제공되는 FastEthernet

총 4개의 포트 사용 가능

2️.네트워크 연결 설계
부서/섹션	서브넷	라우터 인터페이스	연결 대상 (스위치)
Administration	192.168.2.0/24	Fa0/0 (192.168.2.1)	Switch0
Database	192.168.1.0/24	Fa0/1 (192.168.1.1)	Switch3
Finance	192.168.3.0/24	Fa1/0 (192.168.3.1)	Switch1
IT	192.168.4.0/24	Fa1/1 (192.168.4.1)	Switch2
3️.케이블 연결

PC ↔ Switch : Copper Straight-Through

Server ↔ Switch : Copper Straight-Through

Switch ↔ Router (Fa0/0, Fa0/1, Fa1/0, Fa1/1) : Copper Straight-Through

4️.라우터 IP 설정
enable
configure terminal

! Administration
interface fa0/0
 ip address 192.168.2.1 255.255.255.0
 no shutdown

! Database
interface fa0/1
 ip address 192.168.1.1 255.255.255.0
 no shutdown

! Finance
interface fa1/0
 ip address 192.168.3.1 255.255.255.0
 no shutdown

! IT
interface fa1/1
 ip address 192.168.4.1 255.255.255.0
 no shutdown

5️.PC 및 서버 설정 

PC0 (Administration)

IP: 192.168.2.2 / 24

GW: 192.168.2.1

PC1 (Administration)

IP: 192.168.2.3 / 24

GW: 192.168.2.1

Server0 (Database)

IP: 192.168.1.100 / 24

GW: 192.168.1.1

PC2 (Finance)

IP: 192.168.3.2 / 24

GW: 192.168.3.1

PC3 (Finance)

IP: 192.168.3.3 / 24

GW: 192.168.3.1

PC4 (IT)

IP: 192.168.4.2 / 24

GW: 192.168.4.1

PC5 (IT)

IP: 192.168.4.3 / 24

GW: 192.168.4.1
PC0 ↔ PC5, PC ↔ Server0 등 모든 부서 간 통신이 가능
