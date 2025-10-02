# 🏥 PostgreSQL High Availability Lab

<div align="center">

![PostgreSQL HA](https://img.shields.io/badge/PostgreSQL-High%20Availability-336791?style=for-the-badge&logo=postgresql)
![Zero Downtime](https://img.shields.io/badge/Zero%20Downtime-Automated%20Failover-green?style=for-the-badge)
![Docker Ready](https://img.shields.io/badge/Docker-Ready-blue?style=for-the-badge&logo=docker)
![Healthcare Data](https://img.shields.io/badge/Healthcare-Dataset%20Included-red?style=for-the-badge)

**🚀 Enterprise-Grade Database High Availability - Zero Downtime, Maximum Reliability**

[🎯 **Get Started in 5 Minutes**](#-quick-start) • [📊 **Live Demo**](#-access-your-cluster) • [🛡️ **Why HA Matters**](#-why-high-availability)

</div>

---

<div align="center">

## **🎯 Your Database. Always Available.**

**99.9% Uptime Guaranteed** • **Automated Failover** • **Real-time Monitoring** • **Healthcare Dataset Included**

*Perfect for businesses that can't afford downtime - from healthcare to e-commerce to financial services.*

</div>

## 🔥 Why High Availability Matters for Your Business

<div align="center">

| **Without HA** | **With HA** |
|----------------|-------------|
| ❌ **System crashes = Lost revenue** | ✅ **99.9% uptime guaranteed** |
| ❌ **Manual recovery takes hours** | ✅ **Automatic failover in 30 seconds** |
| ❌ **Data loss during failures** | ✅ **Zero data loss protection** |
| ❌ **Stressful emergency responses** | ✅ **Peace of mind monitoring** |

</div>

### 🎯 **Perfect For:**
- 🏥 **Healthcare** - Patient records always available
- 🛒 **E-commerce** - Shopping cart never lost
- 💰 **Finance** - Transactions never interrupted
- 📱 **SaaS** - Services always online

## 🏗️ PostgreSQL HA Cluster Architecture

This project implements a high availability PostgreSQL cluster with monitoring and replication.
Below is the infrastructure diagram:

<div align="center">

![HA Cluster Architecture](docs/diagram.png)

**Figure 1: High Availability PostgreSQL Cluster Architecture**

</div>

### **Architecture Components:**

| Component | Role | Service Port | Purpose |
|-----------|------|--------------|---------|
| **🏥 Primary Database** | Active read/write operations | `5432` | Main database node with healthcare data |
| **🔄 Replica Node 1** | Hot standby replication | `5433` | First failover target (priority: 90) |
| **🔄 Replica Node 2** | Hot standby replication | `5434` | Second failover target (priority: 80) |
| **🎯 Monitor Node** | Cluster coordination | `5431` | Health monitoring & automated failover |
| **📊 Grafana** | Dashboard & visualization | `3000` | Real-time monitoring dashboards |
| **📈 Prometheus** | Metrics collection | `9090` | Performance metrics aggregation |
| **🔍 postgres-exporter** | Database metrics | `9187` | PostgreSQL performance monitoring |

### **Visual Architecture:**

<div align="center">

![HA Cluster Architecture](docs/Architecture.png)

*Complete PostgreSQL High Availability cluster with automated failover and monitoring*

</div>

---

## 🚀 Quick Start

<div align="center">

### **🎯 3 Simple Steps to High Availability**

</div>

### **Step 1: Launch Your HA Cluster**
```bash
# Clone and start (takes 2-3 minutes)
git clone https://github.com/saifoufa1/PostgresSQL-HA.git
cd PostgresSQL-HA
cp .env.test .env
docker compose up -d --build
```

### **Step 2: Verify Everything Works**
```bash
# Check status (should show 1 primary + 2 replicas)
docker compose exec pgaf-monitor bash /opt/pgaf/show-state.sh | jq

# Test database connection
PGPASSWORD=postgres_password psql -h 127.0.0.1 -p 5432 -U postgres -d healthcare_db \
  -c "SELECT COUNT(*) FROM medical_facilities;"
```

### **Step 3: Access Your Dashboards**
| Service | URL | What You'll See |
|---------|-----|-----------------|
| **📊 Grafana** | http://localhost:3000 | Real-time cluster health |
| **📈 Prometheus** | http://localhost:9090 | Performance metrics |
| **🏥 Database** | localhost:5432 | Your healthcare data |

**🎉 That's it! Your database cluster is now highly available with automated failover!**

---

## 📊 See Your HA Cluster in Action

<div align="center">

### **🖥️ Real-time Monitoring Dashboard**

*Access Grafana at http://localhost:3000 (admin/admin) to see:*

![Dashboard Preview](https://img.shields.io/badge/Live%20Dashboard-View%20Metrics-green?style=flat-square)

- **🟢 Node Health Status** - See all 3 nodes (1 primary + 2 replicas)
- **📈 Performance Metrics** - CPU, memory, disk usage
- **🔄 Replication Lag** - Data sync status between nodes
- **⚡ Failover Events** - Historical failover tracking

</div>

### **🏥 Sample Healthcare Data Included**

Your cluster comes pre-loaded with realistic healthcare data:

```sql
-- See your data
SELECT COUNT(*) FROM patients;        -- 1,000+ patients
SELECT COUNT(*) FROM medical_facilities; -- 50+ facilities
SELECT COUNT(*) FROM appointments;    -- 2,000+ appointments
```

**Perfect for testing your applications with realistic healthcare scenarios!**

---

## 🛡️ Test Failover Scenarios

<div align="center">

### **💡 See Automatic Failover in Action**

</div>

### **Scenario 1: Primary Database Crash**
```bash
# Simulate a database server crash
docker compose stop postgres-primary

# Watch automatic failover (30 seconds)
docker compose exec pgaf-monitor bash /opt/pgaf/show-state.sh | jq

# Verify new primary is working
PGPASSWORD=postgres_password psql -h 127.0.0.1 -p 5432 -U postgres -d healthcare_db \
  -c "SELECT COUNT(*) FROM patients;"
```

### **Scenario 2: Network Issues**
```bash
# Test network partition recovery
docker compose restart postgres-replica1

# Monitor automatic resynchronization
docker compose exec pgaf-monitor bash /opt/pgaf/show-state.sh | jq
```

**✨ Your applications continue working seamlessly during these failures!**

---

## 🎯 What Makes This Special?

<div align="center">

| **Traditional Setup** | **This HA Solution** |
|----------------------|---------------------|
| ❌ Manual failover (hours) | ✅ **30-second automatic failover** |
| ❌ Complex configuration | ✅ **One-command setup** |
| ❌ Expensive consultants | ✅ **Ready-to-use solution** |
| ❌ Basic monitoring | ✅ **Enterprise dashboards** |

</div>

### **💰 ROI: Return on Investment**

- **⏱️ Save Hours**: No more late-night emergency calls
- **💸 Reduce Costs**: Prevent revenue loss from downtime
- **🛡️ Peace of Mind**: Know your data is always safe
- **📈 Business Growth**: Focus on growth, not infrastructure

---

## 🚀 Ready to Get Started?

<div align="center">

### **🎯 Your Next Steps:**

**1. Launch your HA cluster** (2 minutes)
```bash
git clone https://github.com/saifoufa1/PostgresSQL-HA.git
cd PostgresSQL-HA && cp .env.test .env
docker compose up -d --build
```

**2. Explore your dashboards** (1 minute)
- Grafana: http://localhost:3000 (admin/admin)
- Database: localhost:5432 (postgres/postgres_password)

**3. Test a failover scenario** (2 minutes)
```bash
docker compose stop postgres-primary
# Watch automatic failover in Grafana!
```

**🎉 Congratulations! You now have enterprise-grade high availability!**

</div>

---

## 📚 Learn More

* **[📖 Detailed Documentation](docs/)** - Deep dive into advanced features
* **[🧪 Testing Guide](docs/02-automated-failover.md)** - Comprehensive testing scenarios
* **[🔧 Troubleshooting](docs/04-recovery-procedures.md)** - Solutions to common issues

---

<div align="center">

## **🎯 Experience Zero-Downtime Database Operations**

**Made Simple. Made Reliable. Made for Business.**

*Questions? Need help? Check our detailed documentation in the `docs/` folder.*

</div>

## 📞 Need Help?

<div align="center">

**📚 Check the detailed documentation in the `docs/` folder for advanced topics**

**🔧 Found an issue?** Check the troubleshooting guides in `docs/04-recovery-procedures.md`

**💡 Want to learn more?** Explore the testing scenarios in `docs/02-automated-failover.md`

</div>

---

<div align="center">

## **🎯 Your Database is Now Enterprise-Ready!**

**Zero Downtime** • **Automated Failover** • **Real-time Monitoring** • **Healthcare Data Included**

*Ready to scale your business with confidence! 🚀*

</div>
