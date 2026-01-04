# VLAN Lab: Inter-VLAN Routing with Router-on-a-Stick

## Objective
Simulate a multi-VLAN network with static IPs and inter-VLAN routing using a 1941 router and three switches.

## Topology Overview
- 3 Switches (Switch1, Switch2, Switch3)
- 9 PCs (3 per switch)
- 1 Router (1941)
- VLANs:
  - VLAN10: Guest
  - VLAN20: Student
  - VLAN30: Staff

## IP Addressing Scheme

| VLAN | Subnet            | Gateway         | PC IPs             |
|------|-------------------|-----------------|--------------------|
| 10   | 192.168.10.0/24   | 192.168.10.1    | .11, .12, .13      |
| 20   | 192.168.20.0/24   | 192.168.20.1    | .21, .22, .23      |
| 30   | 192.168.30.0/24   | 192.168.30.1    | .31, .32, .33      |

##  Configuration Summary

### Router (1941)
- Interface: `GigabitEthernet0/0`
- Subinterfaces:
  - `Gi0/0.10` → VLAN10 → `192.168.10.1`
  - `Gi0/0.20` → VLAN20 → `192.168.20.1`
  - `Gi0/0.30` → VLAN30 → `192.168.30.1`
- Encapsulation: `dot1Q`

### Switch1
- Trunk port: `Fa0/22` → Router
- VLAN assignments:
  - `Fa0/1–5` → VLAN10
  - `Fa0/6–10` → VLAN20
  - `Fa0/11–15` → VLAN30

### Switch2 & Switch3
- Trunked to Switch1
- Same VLAN port layout as Switch1

## /screenshots
  ├── topology_diagram.png
  ├── router_subinterfaces.png
  ├── switch1_trunk_port_fa0_22.png
  ├── vlan_table_switch1.png
  ├── pc_ip_config_vlan10.png
  ├── ping_test_vlan10_to_vlan20.png

## Test Results

- All PCs can ping across VLANs
- Static IPs and gateways correctly assigned
- 0% packet loss
- Latency values are simulated by Packet Tracer

## Files Included

- `vlan_lab.pkt` (Packet Tracer file)
- `screenshots/` folder
- `README.md`

## Notes

> Ping latency in Packet Tracer is simulated and does not reflect real performance. All devices respond successfully.


To open the lab, download vlan_lab.pkt and open it in Cisco Packet Tracer.
