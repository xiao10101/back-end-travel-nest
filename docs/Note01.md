# Prisma CLI 作为开发依赖
npm install prisma --save-dev

# Prisma 客户端 + PostgreSQL 驱动适配器
npm install @prisma/client @prisma/adapter-pg pg

# 初始化 Prisma 项目
npx prisma init --output ../src/generated/prism

# 生成迁移文件并直接执行到数据库
npx prisma migrate dev --name init

# 生成类型化的 Prisma Client
npx prisma generate

# 创建 PrismaService 服务

```TypeScript
@Injectable()
export class PrismaService extends PrismaClient {
  constructor() {
    const adapter = new PrismaPg({
      connectionString: process.env.DATABASE_URL as string
    })
    super({ adapter })
  }
}
```