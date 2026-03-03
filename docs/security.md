# 🔐 安全策略说明

本系统涉及多模型与多供应商，安全控制至关重要。

---

# 一、鉴权策略

## 1️⃣ Gateway Token

```
OPENCLAW_GATEWAY_TOKEN=...
```

必须启用。

---

## 2️⃣ Router 鉴权

所有 upstream 必须声明：

```
auth: bearer:KEY
```

严禁硬编码在代码中。

---

# 二、网络安全

## 推荐设置

```
OPENCLAW_GATEWAY_BIND=loopback
```

避免暴露公网。

---

## Docker 网络隔离

- Router 仅内部访问
- 不暴露真实模型 IP
- 外部 API 通过 Router 访问

---

# 三、密钥管理

- 使用 `.env`
- 提供 `.env.example`
- 不提交真实 Key
- 定期轮换密钥

---

# 四、日志与审计

建议：

- 请求日志记录
- Token 使用统计
- 异常告警
- 审计访问记录

---

# 五、安全设计原则

1. 永远不要让应用层直连供应商
2. 统一通过 Router
3. 禁止硬编码密钥
4. 使用最小权限原则
5. 生产环境禁用非必要端口
